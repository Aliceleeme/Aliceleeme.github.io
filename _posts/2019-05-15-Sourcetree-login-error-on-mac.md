----
title: "Mac에서 Sourcetree 오류 문제 해결하기"
categories:
* Develop
last_modified_at: 2019-05-15T14:00:00+08:00
toc: true
----

## 현상

SourceTree에서 커밋은 가능하지만 푸쉬는 완료되지 못한 상황이다.
GitHub 계정 설정에 실패한 듯 하여 소스트리에서 리모트 레포지토리를 확인해봤더니 GitHub 로그인을 요구했다.
메일 주소와 비밀번호를 입력했더니 아래와 같은 오류가 발생하였다.

Could not authorize request with the available token. Please re-authenticate.


## 해결법

①GitHub 계정의 Personal Setting→ Applications→ Authorized OAuth Apps을 확인

  * SourceTreeForMac(Mac의 경우)가 있는 것을 확인

②SourceTree의 설정 아이콘→ 계정→ GitHub 계정을 재연결

  * 에러는 발생하지 않았고 로그인이 된 것처럼 보이지만 Push 실패

③KeyChain Access의 GitHub Credentials와 github.com Access Key for [계정명]의 패스워드를 삭제→ PC 재부팅→ SourceTree에서 GitHub에 재로그인

  * KeyChain Access 경로:  Application_Utilities_. 매킨토시의 응용 프로그램 폴더의 유틸리티 안에 있다

  * 여기서 말하는 GitHub credentials, github.com access key for X의 패스워드는 아래와 같다. 초보자라면 찾기 쉽지 않을 내용.

![](2019-05-16/mac_keychain.png)

③번의 방법으로 마침내 해결


## 원인

SourceTree가 GitHub Credentials의 비밀번호 액세스 허가 다이얼로그를 중복 발생.
한 번 통상적으로 허가했음에도, 여러번 출력된 다이얼로그를 종료할 수 있는 버튼이 없기 때문에 거부된 채로 종료된 것이 원인이라고 짐작된다.



## 참고링크

[링크1](https://community.atlassian.com/t5/Sourcetree-questions/Getting-quot-Could-not-authorize-request-with-the-available/qaq-p/708633)

[링크2](https://community.atlassian.com/t5/Sourcetree-questions/Authentication-issue-accessing-GitHub-repos/qaq-p/397660)

[링크3](https://stackoverflow.com/questions/23039133/github-sourcetree-getting-unauthorized-error)

[번역 원본(일본어)](https://qiita.com/iKimishima/items/387ccd8b2172c683c5ea)
