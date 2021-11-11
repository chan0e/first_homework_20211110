# first_homework_20211110


# getopt 명령어


## 구문
**getopt** opstsring varname [args...]

![getopts](https://user-images.githubusercontent.com/94053008/141286244-aa801203-9e67-4b2a-8b46-efed2cc46631.png)

[출처 - https://mug896.github.io/bash-shell/getopts.html]

## 설명
**getopt** 명령은 쉘 에서 명령을 실행할 때 옵션을 사용하는데요. 스크립트 파일이나 함수를 실행할 때도 동일하게 옵션을 사용할 수 있습니다. 사용된 옵션은 다른 인수들과 마찬가지로 $1, $2, ... positional parameters 형태로 전달되므로 스크립트 내에서 직접 옵션을 해석해서 사용해야 됩니다. 이때 옵션 해석 작업을 쉽게 도와주는 명령이 **getopts** 입니다.
