프로젝트를 하던중 버그를 발견해서 작성해본다.

* webview 진입 후 localStorage에서 사용자 정보를 가져와 특정 조건을 만족한다면 데이터를 등록할 수 있는 기능이었다.
* 버그가 발생하여 확인해보니 A계정 로그아웃 -> B계정 로그인 -> 페이지 렌더링시 localStorage에서 데이터를 가져온다. <br/> -> 이전 A계정의 정보를 가져옴(?)

# Uncaught SyntaxError: missing ) after argument list

<br>

  ## native -> web단으로 데이터를 메소드의 파라미터로 보내던 중 못넘겨서 발생한 에러
  
  <br>
  
  ![image](https://user-images.githubusercontent.com/94499416/163940242-5fd4675c-0d2c-415b-83f4-0442a79c33dd.png)
  
  * 위 사진은 native -> web으로 데이터를 전달받는 함수이며 string 형태로 파라미터를 native단에서 받아온다.
  * 파라미터를 console.log로 출력해보니 파라미터 하나가 닫는 따옴표가 없어서 발생한 에러
  * 'sub_address과 같이 출력되었다. 곧바로 안드로이드팀과 컨택해 문제점을 빠르게 수정하였다.
  * 따옴표를 제대로 닫지 못하거나 감싸지  생긴 에러.
