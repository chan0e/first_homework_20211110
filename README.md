# first_homework_20211110



# getopt 명령어

## 구문
**getopt** Format Tokens

## 설명
**getopt** 명령은 예상되는 플래그와 인수를 지정하는 형식을 사용하여 토큰 리스트를 구문 분석합니다. 플래그는 단일 ASCII 문자이며 뒤에 :(콜론)이 올 경우 하나 이상의 탭 또는 공백으로 분리하거나 분리할 수 없는 인수가 있어야 합니다. 인수에는 복수 바이트를 포함시킬 수 있지만 플래그 문자로는 포함시킬 수 없습니다.
**getopt** 명령은 모든 토큰을 읽은 후 또는 특수 토큰 -(더블 하이픈)이 발생하는 경우 처리를 완료합니다. 그러면 **getopt** 명령은 처리된 플래그, -(더블 하이픈) 및 남아 있는 토큰을 출력합니다.

토큰이 플래그와 일치하는 데 실패하는 경우 **getopt** 명령은 메시지를 표준 오류에 기록합니다.

### 옵션
Option이란 아래와 같이 Linux 에서 '-'로 시작하는 문자열을 의미합니다.


$./getopt -a

$./getopt -b optarg

$./getopt -b optarg nonopt



# getopts 명령어 
## 구문
**getopt** opstsring varname [args...]

![getopts](https://user-images.githubusercontent.com/94053008/141286244-aa801203-9e67-4b2a-8b46-efed2cc46631.png)

[출처 - https://mug896.github.io/bash-shell/getopts.html]

## 설명
**getopt** 명령은 쉘 에서 명령을 실행할 때 옵션을 사용하는데요. 스크립트 파일이나 함수를 실행할 때도 동일하게 옵션을 사용할 수 있습니다. 사용된 옵션은 다른 인수들과 마찬가지로 $1, $2, ... positional parameters 형태로 전달되므로 스크립트 내에서 직접 옵션을 해석해서 사용해야 됩니다. 이때 옵션 해석 작업을 쉽게 도와주는 명령이 **getopts** 입니다.
