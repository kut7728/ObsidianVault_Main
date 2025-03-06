## Dos and Don’ts

|Dos|Don’ts|
|---|---|
|주특기별 기능 구현 마감 기한을 설정하세요.||
|노션으로 작성하는 API 명세는 러프하게 작성하고, Swagger를 꼭 적용하세요.||

  

---

## 1. API 명세서 작성

#### API 설계 예시

|기능|method|함수|request header|response header|request|response|에러발생시 response|비고|
|---|---|---|---|---|---|---|---|---|
|[[카카오톡으로 로그인]]|UserApi|loginWithKakaoTalk()|||OAuthToken token = await UserApi.instance.loginWithKakaoTalk();|print('카카오톡으로 로그인 성공 ${token.accessToken}');|print('카카오톡으로 로그인 실패 $error');||
|[[카카오 계정으로 로그인]]|UserApi|loginWithKakaoAccount()|||OAuthToken token = await UserApi.instance.loginWithKakaoAccount();|print('카카오계정으로 로그인 성공 ${token.accessToken}');|print('카카오계정으로 로그인 실패 $error');||
|[[로그아웃]]|UserApi|logout()|||await UserApi.instance.logout();|print('로그아웃 성공, SDK에서 토큰 삭제');|print('로그아웃 실패, SDK에서 토큰 삭제 $error');||
|[[카카오 사용자 정보 가져오기]]|UserApi|me()|||User user = await [UserApi.instance.me](http://userapi.instance.me/)();|print('사용자 정보 요청 성공'  <br>'\n회원번호: ${  <br>[user.id](http://user.id/)}'  <br>'\n닉네임: ${user.kakaoAccount?.profile?.nickname}'  <br>'\n이메일: ${user.kakaoAccount?.email}');|print('사용자 정보 요청 실패 $error');||
|[[연결끊기(회원탈퇴)]]|UserApi|unlink()|||await UserApi.instance.unlink();|print('연결 끊기 성공, SDK에서 토큰 삭제');|print('연결 끊기 실패 $error');||
|[[네이버 지도]]|UserApi||||await NaverMapSdk.instance.initialize(clientId: "your client id");||await NaverMapSdk.instance.initialize(  <br>clientId: 'your client id',  <br>onAuthFailed: (ex) {  <br>print("********* 네이버맵 인증오류 : $ex *********");  <br>});||
|[[카카오톡 알림 전송]]|UserApi|[sendDefaultMemo()](https://developers.kakao.com/docs/latest/ko/message/flutter#default-template-msg-me)|||await TalkApi.instance.sendDefaultMemo(defaultFeed);|MessageFailureInfo|print('나에게 보내기 실패 $error');||

  
  

  

## 2. ERD 다이어그램 설계

- ERD 예시
    
    ![[ERD_최종.png]]
    
      
    
      
    
    - 제작한 ERD 다이어 그램  
          
        
        ![[Assets/Untitled 2.jpeg|Untitled 2.jpeg]]