# first_homework_20211110



# getopt 명령어

## 구문
**getopt** Format Tokens

## 설명
**getopt** 명령은 예상되는 플래그와 인수를 지정하는 형식을 사용하여 토큰 리스트를 구문 분석한다. 플래그는 단일 ASCII 문자이며 뒤에 :(콜론)이 올 경우 하나 이상의 탭 또는 공백으로 분리하거나 분리할 수 없는 인수가 있어야 한다. 인수에는 복수 바이트를 포함시킬 수 있지만 플래그 문자로는 포함시킬 수 없다.
**getopt** 명령은 모든 토큰을 읽은 후 또는 특수 토큰 -(더블 하이픈)이 발생하는 경우 처리를 완료한다. 그러면 **getopt** 명령은 처리된 플래그, -(더블 하이픈) 및 남아 있는 토큰을 출력.

토큰이 플래그와 일치하는 데 실패하는 경우 **getopt** 명령은 메시지를 표준 오류에 기록.



## case로 분류한 코드

```shell script
#!/bin/bash

if ! options=$( getopt -o a:bc -l help,path:,name: -- "$@" )
then 
    echo "ERROR: print usage"
    exit 1
fi

eval set -- "$options"

while true; do
    case "$1" in
        -h|--help)
            echo >&2 "$1 was triggerd!"
            shift ;;
        -p|--path)
            echo >&2 "$1 was triggered!, OPTARG: $2"
            shift 2 ;; # 옵션이 argument가 있으므로 shift 2
        -n|--name)
            echo >&2 "$1 was triggered!, OPTARG: $2"
            shift 2 ;;
        --aaa)
            echo >& "$1 was triggered!"
            shift ;;
        --)
            shift
            break
    esac
done

echo -------------
echo "$@"
```




# getopts 명령어 
## 구문
**getopt** opstsring varname [args...]

![getopts](https://user-images.githubusercontent.com/94053008/141286244-aa801203-9e67-4b2a-8b46-efed2cc46631.png)

[출처 - https://mug896.github.io/bash-shell/getopts.html]

## 설명
**getopts** 명령은 쉘 에서 명령을 실행할 때 옵션을 사용한다. 스크립트 파일이나 함수를 실행할 때도 동일하게 옵션을 사용할 수 있다. 사용된 옵션은 다른 인수들과 마찬가지로 $1, $2, ... positional parameters 형태로 전달되므로 스크립트 내에서 직접 옵션을 해석해서 사용해야 된다. 이때 옵션 해석 작업을 쉽게 도와주는 명령이 **getopts** 이다.



## Short 옵션 특징
* '-'로 시작하는 short한 옵션
   * -p

* 여러가지 방법으로 사용가능
* 순서에 상관없음
* 옵션 argument를 가질수 있고 붙여 쓸 수 있음


    $cmd -a -b -c 

    $cmd -abc
    
    $cmd -b -ac
    
    
## long 옵션 특징
* '--'가 붙은 long 옵션
   * --posix,--wrning level 등

## getopt사용
1) short option은 '-o'를 사용하여 아래와 같이 사용한다.

   1)-1 option은 그냥 나열하면 된다.
  
   1)-2 argument를 가지는 옵션은 ':'를 뒤에 붙인다.
 
  **getopt -o a:bc # 위의 getopts와 똑같다. -a, -b, -c 를 옵션으로 가지고 -a는 argument가 있다.**
  
***
  
2) long option은 '-l'을 사용하고 ','로 구분한다.

   2)-1 option은 ','로 구분한다
  
   2)-2 argument를 가지는 옵션은 ':'를 뒤에 붙인다.
 
  **getopt -l help,path:,name:**
  
  **--help**
  
  **--path 'argument'    --path='argument'**
  
  **--name 'argument'    --name='argument'**

***
3) short, long 공통

    3)-1 마지막에 --"$@" 를 붙인다.
    
    3)-2  invalid option 이나 argument가 빠진경우 오류메세지를 출력한다.
    

## loop 문을 이용해 처리


```shell script
#!/bin/bash

while getopts "a:bc" opt; do
  case $opt in
    a)
      echo >&2 "-a was triggered!, OPTARG: $OPTARG"
      ;;
    b)
      echo >&2 "-b was triggered!"
      ;;
    c)
      echo >&2 "-c was triggered!"
      ;;
  esac
done

shift $(( OPTIND - 1 ))
echo "$@"
```

```
..................................
$ ./test.sh -a xyz -bc hello world
-a was triggered!, OPTARG: xyz
-b was triggered!
-c was triggered!
hello world
```


## Error reporting
위 예제에서 옵션 스트링에 없는 문자, 예를 들면 -d 를 사용하게 되면 오류 메시지가 출력되는 것을 볼 수 있는데
getopts 명령은 error reporting 과 관련해서 다음과 같은 두 개의 모드를 제공한다.


|**Verbose mode** |  |
|----------------|---|
|invalid 옵션사용|opt 값을 '?'문자로 설정하고 OPTARG 값은 unset. 오류 메세지를 출력|
|옵션인수 값을 제공 하지않음|opt값을 '?'문자로 설정하고 OPTARG 값은 unset. 오류 메세지를 출력|


|**Silent mode** |  |
|----------------|---|
|invalid 옵션사용|opt 값을 '?'문자로 설정하고 OPTARG 값은 해당 옵션 문자로 설정|
|옵션인수 값을 제공 하지않음|opt값을 '?'문자로 설정하고 OPTARG 값은 해당 옵션 문자로 설정|


default 는 verbose mode 인데 기본적으로 옵션과 관련된 오류메시지가 표시되므로 스크립트를 배포할 때는 잘 사용하지 않고 대신 silent mode 를 이용. silent mode 를 설정하기 위해서는 옵션 스트링의 맨 앞부분에 ':' 문자를 추가.



---


# sed 명령어

## 구문
sed 's/c찾을텍스트/바꿀텍스트/' 파일명

## 설명
ed명령어와 grep명령어 기능의 일부를 합친 것이 sed(stream editor)명령어 이다. sed는 각 라인을 읽을 때마다 대치작업을 실행한다.
일치하는 문자열이 있으면 그 문자열을 대치한 후 출력하고 일치하는 문자열이 없으면 그 라인은 수정되지 않고 그대로 출력된다.
또한 sed명령어는 ed보다 좋은 점은 라인들을 하나씩 읽고, 수정하고, 출력하기 때문에 기억장치 안의 버퍼를 사용하지 않는다 것이다.
즉, 파일의 크기에 제한 없이 작업을 할수 있다. 그리고 sed 명령어는 아주 큰 파일을 처리할 때 주로 사용된다.

## sed 명령어 사용법

1) 치환(substitute)

**sed 's/Hi/hello/' list.txt** 

-> Hi를 hello로 바꾼다. 허나 원본 파일을 바꾸지 않고 표준출력만 한다.

**sed 's/\t/\ /' list.txt**

-> 탭문자를 엔터로 변환

---


2) 삭제(delete)

sed '/TD/d' 1.html : TD 문자가 포함된 줄을 삭제하여 출력한다.

sed '/Src/!d' 1.html : Src 문자가 있는 줄만 지우지 않는다.

sed '1,2d' 1.html : 처음 1줄, 2줄을 지운다.

**sed '/^$/d 1.html : 공백라인을 삭제하는 명령이다.** 


# awk 명령어

## 구문

**awk [OPTION...] [awk program] [ARGUMENT...]**

## 설명
**awk**는 파일로부터 레코드를 선택하고, 선택된 레코드에 포함된 값을 조작하거나 데이터화하는 것을 목적으로 사용하는 명령어이다.
즉,**awk** 명령의 입력으로 지정된 파일로부터 데이터를 분류한 다음, 분류된 텍스트 데이터를 바탕으로 패턴 매칭 여부를 검사하거나
데이터 조작 및 연산 등의 액션을 수행하고, 그 결과를 출력하는 기능을 수행한다.

awk 명령으로 아래와 같은 일들을 할수 있다.

* 텍스트 파일의 전체내용 출력
* 파일의 특정 필드만 출력
* 특정 필드에 문자열을 추가해서 출력
* 패턴이 포함된 레코드 출력
* 특정 필드에 연산 수행 결과 출력
* 필드 값 비교에 따라 레코드 





