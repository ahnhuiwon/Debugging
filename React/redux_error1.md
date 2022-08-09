## Redux

### `[react-redux] Error: You must pass a component to the function returned by connect. Instead received {}`

react-redux 에서 connect 함수 사용시 제대로 코딩하지 않아서 나는 오류

아래는 수정전 코드이다.

``

export default connect(
  state => ({
    number: state.counter,
  }),
  { up_count, down_count }
)

```

이렇게 코딩을 하니 다음과 같은 오류발생

Error: You must pass a component to the function returned by connect. Instead received {}

 

Component를 넘겨주지 않아서 그렇다. 다음과 같이 컴포넌트도 넘겨줘야 한다. 결국은 실수로 일어난 에러.

제대로 쓰는 방식은 다음과 같다.

```

export default connect(
  state => ({
    number: state.counter,
  }),
  { up_count, down_count }
)(CounterContainer)

```
