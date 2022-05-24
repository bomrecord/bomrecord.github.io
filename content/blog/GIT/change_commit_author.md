---
title: '이전 commit의 author 변경'
date: 2022-03-16 03:24:15
category: 'GIT'
draft: false
---

깃 커밋을 했는데 잔디가 표시되지 않아서 찾아보았더니 회사의 아이디로 커밋이 되었다.

이전 커밋의 author를 변경하기 위한 명령어를 기록한다.

### 1\. rebase 명령어로 바꿀 커밋을 선택해준다.

rebase 명령어 세 가지를 소개한다. 

**최신 커밋으로부터 5번째 커밋을 바꾸고 싶을 때**

```
$ git rebase -i HEAD~5
```

**수정하고자 하는 커밋의 직전커밋 해쉬를 알고있을 때**

```
$ git rebase -i -p 3dc6a06
```

**최초의 커밋을 수정하고자 할 때**

```
$ git rebase -i --root
```

### 2\. author를 바꿀 commit의 pick을 e로 변경하여 저장한다. 

### 3\. 변경할 author를 입력한다. 

author에는 "아이디 <이메일>" 형식으로 기입한다.

```
$ git commit --amend --author="chunnycode <chunnycode@gmail.com>"
```

### 4\. rebase를 완료시키고 push한다. 

```
$ git rebase --continue
$ git push -f origin master
```

github의 잔디에도 표시가 되었음을 확인할 수 있다.

보다 편리한 git 생활을 위해 개인프로젝트 폴더는 git user 설정을 다르게 해두었다.

간단하게 처리된다.