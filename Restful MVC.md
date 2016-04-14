##**MVC**
MVC란 Model View Controller 의 약자로 어플리케이션의 역할을 나눈 개발 방법이다.
> * Controller : 사용자의 요청사항에 따라 해당하는 Model을 호출하여 사용자가 원하는 값을 View에 보여주는 역할을 한다.
> * Model : 데이터 담당 즉, 데이터 베이스를 통해 데이터를 가공하는 역할을 한다.
> * View : javascript/html/css 클라이언트를 모아둔 컨테이너이다.

##**Restful API**

Restful은 ROA를 따르는 웹 서비스 디자인 표준이다. 기존엔 세션을 이용하여 처리하였다면 REST는 세션을 사용하지 않기때문에 독립적이고 각각의 요청은 이전의 요청과 무관하게 처리할 수 있다.

>**ROA 속성**

>+ Addressablilty
 - 제공하는 모든 정보를 URI로 표시할 수 있어야 한다.
   ex) URL : http://www.google.com/index.jsp?id=1
       URI : http://www.google.com/id/1
 - 하이퍼링크를 다라서만 해당 리소스에 접근하지 않고 직접 URI로 접근할 수 있다.
 
>+ Connectedness
 - 하나의 리소스들은 서로 주변의 연관 리소스들과 연결되어 표현되어야 한다.

>+ Statelessness
 - 현재 클라이언트의 상태를 절대로 서버에서 관리하지 않아야 한다.
 - 모든 요청은 일회성의 성격을 가지며 이전의 요청에 영향을 받지 말아야 한다.
 - 세션을 유지 하지 않기 때문에 서버 로드 발란싱이 매우 유리하다.
 - URI에 현재 상태를 표현할 수 있어야 한다.

>+ Homogeneous Interface
 - HTTP에서 제공하는 기본적인 4가지의 method와 추가적인 2가지의 method를 이용해서 리소스의 모든 동작을 정의한다.
 -  GET : 리소스 조회
 -  POST : 새로운 리소스 생성
 -  PUT : 존재하는 리소스 변경
 -  DELETE : 존재하는 리소스 삭제
 -  HEAD : 존재하는 리소스 메타데이터 보기
 -  OPTION : 존재하는 리소스의 지원 method 체크

##**javadoc**
javadoc은 API를 쉽게 만들도록 도와준다. 자바 소스 안에 javadoc주석을 사용하여 간편하게 API를 만들 수 있다.

>**사용방법**
>
/ * *            */ 주석 : Class 바로 위에 선언한다.
@param : 파라미터 설명
@return : 리턴값 설명
@version : 클래스 또는 메소드 버전 정보
@author : 작성자 정보
@since : 소스코드가 적용된 버전 정보

>* 사용 예
/* *
   문자를 split 합니다. (클래스 또는 메소드 설명)
   @param str - 문자    
   @return 바꿔진 문자    
   @aothor Gong Hyoseon
   @version 1.0
  */
  public String replace (String str) {
        String[] strSplit = str.split(",");
	String strRslt = "";
	for(int i = 0; i < strSplit.length; i++) {
		strRslt += strSplit[i];
	}
	return strRslt;
}