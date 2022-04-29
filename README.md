# 📚NomadCoder ReactJS 

## Day1. 2021.04.28

### What is the deifference between Reactjs and vanliaJS!
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

## Day2. 2021-04-29
### How to use JSX?
- 그거아시나요? 어제 실무자들은 어제 배웠던 방법으로 요소를 생성하지 않습니다!
- JSX를 통해 개발자처럼 요소를 생성해봅시다. JSX가 뭐냐구요? 

#### JSX는 JavaScript를 확장한 문법입니다.
아래와 같이 변수 선언과 동시에 hmtl문법을 같이 써버립니다.
```jsx
const element = <h1>Hello, world!</h1>;
```

JSX를 사용하여 컴포넌트를 만들어 주면 html안에 컴포넌트를 추가 할 수 있습니다

#### 컴포넌트 만들기
방법은 간단합니다! 변수를 함수로 바꾸어 주면 됩니다!
✍ 컴포넌트의 첫글자는 꼭 대문자로 지정해줍니다. 안그러면 hmtl로 인식해버려요!
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

#### 컴포넌트, 컴포넌트안에 추가하기 
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



