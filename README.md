# 📚NomadCoder ReactJS 

## Day1. 2021.04.28

### What is the difference between Reactjs and vanliaJS!
- 자바스크립트는 html 생성 후 eventlistner를 만들어 줍니다. 
하지만 ReactJS의 경우 html을 생성할 필요 없이 변수를 만들어 바로 eventListner를 추가해 줄 수 있습니다. 
#### React.JS

```jsx
// React.createElement("요소",{property}, "content");
//property작성 칸에 eventlistener도 추가해 줄 수 있다. 변수 지정과 함께 함수도 지정 가능 
//property의 구분은 쉼표로 해준다

const btn = React.createElement(
    "button",
    {
      onClick:()=> console.log("i'm clicked"),
      style:{color:"blue", backgroundColor:"white"},
    },
    "Click me");

//ReactDOM.render(요소,저장위치) = 화면에 보여주기 위해 랜더
ReactDOM.render(btn,root);
```

#### VanilaJS

```jsx

const btn = document.querySelector("#click_btn");

function handleClick(){
  console.log("clicked!");
}

btn.addEventListener("click", handleClick)
```
<br>
<br>

## Day2. 2021.04.29
### How to use JSX?
- 그거아시나요? 어제 실무자들은 어제 배웠던 방법으로 요소를 생성하지 않습니다!
- JSX를 통해 개발자처럼 요소를 생성해봅시다. JSX가 뭐냐구요? 
<br/>

#### JSX는 JavaScript를 확장한 문법입니다.
아래와 같이 변수 선언과 동시에 hmtl문법을 같이 써버립니다.
```jsx
const element = <h1>Hello, world!</h1>;
```
<br/>

#### 컴포넌트 만들기
JSX를 사용하여 컴포넌트를 만들어 주면 html안에 컴포넌트를 추가 할 수 있습니다.</br>
방법은 간단합니다! 변수를 함수로 바꾸어 주면 됩니다!<br/>
#### ✍ 컴포넌트의 첫글자는 꼭 대문자로 지정해줍니다. 안그러면 hmtl로 인식해버려요!

```jsx
    const Title = ()=> ( 
      <h3 id="title" onClick={()=>console.log("title")}> 
        Title
      </h3>);
    
    const Btn = ()=>(
    <button onClick={()=>console.log("btn clicked")}> 
      Click me! 
    </button>);
```

#### 컴포넌트, 컴포넌트 안에 추가하기 
이렇게 `</>`로 컴포넌트 명을 써서 추가해주면 끝입니다! 

```jsx
    //생성요소 div에 추가하기 
    //추가를 위해 요소를 함수로 만들어주기 = 컴포넌트 만들어주기
    //주의!!! : 컴포넌트의 첫글자는 반드시 대문자! 소문자는 html로 인식
    const Container = ()=>(
      <div> 
        <Title />
        <Btn /> 
      </div>
    );
```
<br>
<br>

## Day3. 2021.04.30
### Let's make a counter! (React.useState())
오늘을 카운터를 만들어봅니다. 
어제는 JSX를 이용해 함수를 적용하는 것을 배웟습니다. 오늘은 함수를 적용하고 실제로 UI값도 실시간으로 바꿔봅시다.
먼저 원리를 이해하기 위해 "좋지않은 방법"으로 코드를 생성합니다. 

#### 👎not a good way 
👁‍🗨 React는 interactive가페이지 장점인 만큼 전체를 리랜더해도 수정된 부분만 골라서 리랜더합니다!

```jsx
    let count = 0;
    function countUp(){
      count++;
      reRender();
    }
    
    //render Function
    function reRender(){
      //UI 업데이트를 위해 다시 랜더해준다
      ReactDOM.render(<Container/>,root);
    }
```
<br>

#### 💡 잠깐만요! 배열의 요소 하나하나에 변수를 작성하기 지치신 당신에게 선물...⭐
``` jsx 
const arr[1,2,3]
const [index0, index1, ..] = arr

//이것은 아래의 코드와 동일합니다! 

const index0 = arr[0];
const index1 = arr[1];

```
<br>

하지만 그렇다고 해도 함수 하나 만들때마다 계속 랜더함수 불러오는거.. 귀찮지 않나요? 
그렇다면 State()를 사용해봅시다! 

#### 👍 perfect way! 
``` jsx 
  function Container() {
      //
      const [counter, setCounter] = React.useState(0); 
      //React.useState(0): array를 반환해 주는데 인덱스0:data값, 인덱스: 적용할 함수

      //왜 modifier(setCounter)가 필요한가요?
      //하나하나 리랜더하지않아도 modifier에 값을 지정해주면 자동으로 업데이트 해줍니다! 
      const onClick = () =>{
        setCounter(counter+1);
      };

      return(
        <div> 
          <h3>count : {counter}</h3>
          <button onClick={onClick}>Click me!</button>
          </div>
      )
    };
```
이렇게 
React.useState(); 를 이용하면 render 함수를 불러올 필요 없이 알아서 수정된 값을 리턴값에 반환 시켜 랜더해줍니다. 

