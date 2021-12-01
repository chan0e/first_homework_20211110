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

***

### #2  문제

$ vimgolf put 603ba26a01b4d00009c10a49



![vim-과제-_2](https://user-images.githubusercontent.com/94053008/144227404-da050278-e273-43c5-81d3-f9963060837e.gif)


#### 문제풀이

명령어 %s/sublime\|emacs/vim/g|x

%s/단어/바꿔질단어/g: 단어를 찾아 전체 단어를 바꿔줄 단어로 바꿔줌

x: 변경된 내용을 저장하고 나감

***


### #3  문제



![vim-과제-_3](https://user-images.githubusercontent.com/94053008/144228034-cd5cb5f2-2ecd-43a5-8360-d9962c960558.gif)


#### 문제풀이


![image](https://user-images.githubusercontent.com/94053008/144231473-21aa3d0f-e0d3-4b7c-9385-1eb77e4a1c33.png)


ctrl + e: 한줄씩 위로 이동

i: 입력

%s/str/replace_str: 단어를 바꿔줌

yy: 커서가 있는 그 줄의 문장전체를 복사함

p: 커서가 있는곳 아래로 붙여넣기

x: 변경된 내용을 저장하고 나감

***

### #4  문제



![vim-과제-_4](https://user-images.githubusercontent.com/94053008/144231200-67009acb-8bb5-431b-b9d6-560f9ae73f26.gif)


#### 문제풀이


![image](https://user-images.githubusercontent.com/94053008/144231990-9edb614a-1cf3-4dc9-ad68-1da6b953f28d.png)

G: 글의 맨끝으로 이동

end: 커서가 있는 행의 맨끝으로 이동

x: 변경된 내용을 저장하고 나감

***

### #5  문제



![vim-과제-_5](https://user-images.githubusercontent.com/94053008/144233056-2ebeaf1d-494c-4f46-81f8-3364a7d8ae49.gif)




#### 문제풀이

/ + 단어: 해당하는 단어를 찾아주고 하이라이트 표시가 됌

%s/str/replace_str: 단어를 바꿔줌


5번의 문제는 대략 / + 단어를 이용해 숫자들을 증가 시켜주고, k를 변경해주는대 있어서 문자들을 하나씩 바꿔주었다.
y1 -> abs(y1)으로 바꿔줄땐 %s/str/replace_str를 사용해주었고 이 역시 또한 / + 단어를 이용해 숫자들을 하나씩 바꿔주었다.





**이번 vim 과제는 최고점과 가깝게, 타자수가 작게 푸는거에 집중하기보다는 vim의 명령어들을 최대한 쓸려고 노력했고 굉장히 미숙하고 어려웠던거같다.** 




