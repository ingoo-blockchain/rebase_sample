# 과거커밋 수정

그전에 자꾸 nano 에디터가 열어져서 짜증났던 에디터를 바꿔봅시다.
```sh
$ git config --global core.editor "vi"
```

이번에 배울 rebase -i 는 
총 4가지 기능에 대해서 해볼거에요.

커밋 메시지 변경
커밋 삭제
커밋 합치기
커밋 나누기


**문법**
```sh
$ git rebase -i [수정할 커밋의 이전해시]
```


```sh
git rebase -i [커밋해시]
```


**명령어**
- p, pick : 커밋 그대로 두기
- r, reword : 커밋 메시지 변경
- e, edit  : 수정을 위해 정지 커밋 나누기
- d, drop  : 커밋 삭제
- s, squash : 이전 커밋에 합치기


## 커밋메시지 변경하기
리스트페이지 완성~ 메시지를 r 을 활용하여 해결

```sh
$ git rebase -i 624fd38702d54fce0fbae08d05bbb6d52767695c
```

## 커밋 삭제
test.html 에 해당하는 커밋을 

```sh
$ git rebase -i eadb1c828ab7a7e888b5afdae239c4cf731d0a76
```

d 입력

## 커밋 합치기
수정_1 , 수정_2 커밋을 합치기
```sh
$ git rebase -i acd0a304dd32176ae450d5f0afa5777e8aa3c775
```


## 커밋나누기
완성했따~~ 는
view.html, write.html 이 합쳐져있어요 나눠봅시다.
e 를 활용하여 멈추게한다음에.
git reset HEAD^ 또는 git reset HEAD~1 통해 repository 에있는 내용을
working directory로 이동시켜봅니다.
이후 

따로따로 커밋이후 

rebase --continue 


## 참고

git rebase 는 이전 커밋 히스토리를 변경하는것 이기 떄문에. 정말 조심해야합니다.
그리고 이미 github 같은 원격 저장소에 push 된 상태라면 더더욱 조심해야하며,
만약 그래도 불구하고 꼭 써야할 상황이 온다면

```sh
git push --force 
# 또는
git push -f
```

강제로 커밋을 덮어씌어야합니다.
이런 상황은 다른 협업 개발자와 이슈가 생길수있으니, 꼭 사전에 이야기하고 사용해야합니다.