### [ redux 용어 정리 ]
1. **store** : 어플리케이션의 정보들을 저장하는 저장소
------
2. **state** : 실제 정보(직접 접근이 불가능함)
3. **reducer** : 정보를 공급해주는 역할(함수 형태)

``` js
function reducer(oldState, action) {
    // 현재 값인 state를 받고 action을 참조하여 새로운 state 값을 만들어내서 전달하는 가공자
    if(action.type === 'create') {
        //create 관련된 소스 작성
        return Object.assign({}, state, { // state의 새로운 값을 반환
            /* 
                [Object 복제하는 법]
                * Object.assign() : Object 복사
                [형식]
                인자1 : 꼭 빈 객체
                인자2 : 복제할 속성
                인자3 : 추가할 속성
                Object.assign({}, 복제할 속성, 추가할 속성)
            */
            
        });
    }
}
var store = Redux.createStore(reducer); // store 최초 생성
``` js

4. **dispatch** : 
  4-1. reducer를 호출해서 state 값을 변경 후
  4-2. subscribe를 통해 rander 함수를 호출하여 UI를 변경
   
``` js
store.dispatch(action 값);
```

5. **subscribe** : state 값이 변경될 때마다 rander 함수가 실행되면서 UI가 갱신

``` js
store.subscribe(render);
```

6. **getState** : state 값을 꺼내주는 역할
------
7. **render** : UI를 만들어주는 역할(우리가 짤 코드)
``` js
function render() {
    var state = store.getState();
    //....
    document.querySelector('#app').innerHTML = 
        <h1>WEB</h1>
        ...
}
```

8. **action** : store에 전달할 객체(action 값을 dispatch에게 전달됨)
``` js
{type: 'create', payload: {title:title, desc:desc}};
```
