# Second_homework_20211205

### #1  문제

$ vimgolf put 5f0f5fbe280fbf000c233304



![vim-과제-_1](https://user-images.githubusercontent.com/94053008/144223035-61c4409c-796b-4805-84ea-d5347e4edfa0.gif)


#### 문제풀이

명령어 G -> W -> i -> end -> ESC -> x 


G: 파일의 마지막 줄로 이동 

W: 공백을 포함한 다음문자 뒤로 커서가 이동함

i: 입력하기

end: 그 줄에 끝으로 이동

x: 변경된 내용을 저장하고 나감


### #2  문제

$ vimgolf put 603ba26a01b4d00009c10a49



![vim-과제-_2](https://user-images.githubusercontent.com/94053008/144227404-da050278-e273-43c5-81d3-f9963060837e.gif)


#### 문제풀이

명령어 %s/sublime\|emacs/vim/g|x

%s/단어/바꿔질단어/g: 단어를 찾아 전체 단어를 바꿔줄 단어로 바꿔줌

x: 변경된 내용을 저장하고 나감


### #3  문제



![vim-과제-_3](https://user-images.githubusercontent.com/94053008/144228034-cd5cb5f2-2ecd-43a5-8360-d9962c960558.gif)


#### 문제풀이



![image](https://user-images.githubusercontent.com/94053008/144229069-25f24f3d-63d5-40a4-a0ca-180eb90bb1a4.png)


ctrl + e: 한줄씩 위로 이동

i: 입력

%s/str/replace_str: 단어를 바꿔줌

yy: 커서가 있는 그 줄의 문장전체를 복사함

p: 커서가 있는곳 아래로 붙여넣기

