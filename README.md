# k-busniess
## firebase web project - comstudynews@gmail.com


구글 Cloud Firestore 사용

파이어베이스에 Functions 설정은 https://cafe.naver.com/comstudy21/12778 참고.

데모버전 : http://k-busniess.web.app/user
소스관리 : https://github.com/beomjoon0369/k-busniess

구글 파이어베이스 도움말 : 
https://firebase.google.com/docs/firestore/manage-data/add-data?hl=ko



## Cloud Firestore 보안 규칙
**"규칙" 탭에서 아래 설정을 하고 [게시]**
```
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth.uid != null;
    }
  }
}
```

## NoSQL 계통의 데이터 구조
data가 모여 document가 되고 document를 모아서 collection이 된다.


## 데이터베이스 입력하기(create)
**입력방식에는 Set과 runTransactions가 있다.**
기본적인 데이터 입력 방식은 Set이며 
여러 클라이언트로 부터 데이터 중복 접근 방지를 위해서는 runTransactions를 사용.

**도큐먼트 이름 생성 방식은 직접 입력 방식과 자동 생성 방식이 있다**
도큐먼트 이름 자동 생성하려면 set 대신 add()함수 사용.

```
var docRef = db.collection('users').doc('alovelace');

var setAda = docRef.set({
  first: 'Ada',
  last: 'Lovelace',
  born: 1815
});
```
