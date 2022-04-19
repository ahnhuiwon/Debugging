클라이언트 요청에 따라 수정 작업을 하던 중 오류가 발생하였다.

# Uncaught SyntaxError: missing ) after argument list

<br>

  ## native -> web단으로 데이터를 메소드의 파라미터로 보내던 중 못넘겨서 발생한 에러
  
  <br>
  
  ![image](https://user-images.githubusercontent.com/94499416/163940242-5fd4675c-0d2c-415b-83f4-0442a79c33dd.png)
  
  * 위 사진은 native -> web으로 데이터를 전달받는 함수이며 string 형태로 파라미터를 native단에서 받아온다.
  * 파라미터를 console.log로 출력해보니 파라미터 하나가 닫는 따옴표가 없어서 발생한 에러
  * 'sub_address과 같이 출력되었다. 곧바로 안드로이드팀과 컨택해 문제점을 빠르게 수정하였다.
