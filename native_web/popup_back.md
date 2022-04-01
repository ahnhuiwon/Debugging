# Native WebView
  ## 팝업창 존재시 뒤로가기하면 인터넷 창이 닫히는 이슈
  
    * native webview 프로젝트중 팝업창이 존재해도 뒤로가기 버튼 클릭시 인터넷 창이 닫히는 문제가 생겼다.    
    * 안드로이드는 view단이 스택으로 쌓이는 구조라 뒤로가기가 문제가 없겠지만... react로 구성된 웹은 골치가 아프다.
    * 구글링을 시도한 결과 답은 있었다. 한번 코드를 살펴보자.
    
  
  ## Problem
  
    * 프로젝트로 구성된 웹페이지는 React에 react-router-dom을 사용하여 SPA로 구성하고 있다.
    * 팝업창이 스택 구조로 쌓이는 안드로이드와는 달리 React는 한 화면에서 view단을 계속 그려준다.
    * 위와 같은 이유로 인해 React로 구성된 webview에서 뒤로 가기 버튼을 누르면 페이지 단이 종료하는 것이다.
    
  ## Solution
  
    ![image](https://user-images.githubusercontent.com/94499416/161229998-8a86e301-1885-4f86-af07-b8231e5a54f9.png)
    
    * modal_mode는 팝업창 true / false로 구성된 state값이며 팝업창의 display를 감지한다.
    
    ![image](https://user-images.githubusercontent.com/94499416/161230065-b8200b31-2f4b-4def-ab7a-e630a5269739.png)

    * 팝업창이 출력된 상태(true)라면 히스토리 스택에 현재의 페이지 url을 넣어준다.
    * 뒤로가기 버튼을 누르면 window.onpopstate 이벤트가 감지되어 history.back()을 통해 쌓은 스택을 제거한다.
    * modal_mode의 상태값을 false로 변경해 팝업창을 닫아준다.
    
    ![image](https://user-images.githubusercontent.com/94499416/161230108-c4b56e79-7327-4568-b0b7-b0fe79d846af.png)

    * modal_mode의 값이 false라면 팝업창이 출력되지 않았다는 말이니 정상적으로 뒤로 가야한다.
    * 히스토리 스택을 쌓지않고 뒤로가기 버튼을 눌러 window.onpopstate 이벤트를 감지한다면 history.back()을 통해 뒤로간다.
