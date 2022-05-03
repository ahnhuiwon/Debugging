# React
  ## 카카오 우편번호 api error 

  * 역시 편하게 되는것은 없다... 무엇이 문제인지 구글링을 해보고 다음에 이런 일이 생기면 바로 수정할 수 있게 기록해봤다.

  
  ## error 코드

  ![image](https://user-images.githubusercontent.com/94499416/166423799-34affa83-3906-4041-8d8d-8a207168bd9d.png)
  
    * 작성된 코드에서 나타난 문제는 아니였다.
    * 리액트에서도 사용할 수 있는 패키지를 다운받고 그 컴포넌트를 불러온게 다일 뿐더러 평소엔 문제 없다가 이 컴포넌트가 렌더링이 될때 에러를 출력하는게 문제였다.


  ## 무엇이 문제였는가?
  
  ![image](https://user-images.githubusercontent.com/94499416/166424083-4639380a-dee7-485a-b290-0e31e5ef2386.png)
    
    * 바로 <React.StrictMode>라는 코드가 문제였다, 이 코드를 지우자 잘 작동했다.
    * 대체 이 녀석이 무엇을 하는 코드길래 이러한 문제를 발생시킨걸까?

  ## React.StrictMode?
  
  ![image](https://user-images.githubusercontent.com/94499416/166424430-21b8c733-3b86-4f04-934e-615c2f72ea52.png) <br/>
  ![image](https://user-images.githubusercontent.com/94499416/166424454-fe63ea9f-6eba-4e3c-9369-2b3213392203.png)
  
    * 리액트 입장에서 카카오 우편번호 컴포넌트가 문제여서 이런 오류를 발생했나보다.
    
  ## 해결 
  
  <img width="672" alt="function (1)" src="https://user-images.githubusercontent.com/94499416/166424776-fd508988-807f-45ab-bbc1-4ba47ea96a5d.png">
  
    * <React.StriceMode> 태그를 지운다.
