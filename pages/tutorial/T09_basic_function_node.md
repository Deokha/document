---
title: Function 노드 사용하기 
keywords: Function 노드 사용하기
tags: [tutorial, chatflow, advanced]
sidebar: tutorial_sidebar
permalink: basic_function_node.html
folder: tutorial
summary: Function 노드의 개념을 이해할 수 있습니다.
search: exclude
previous: {
    title: API 노드 사용하기,
    url: basic_api_node.html
}
next: {
    title: 피자주문봇 만들기,
    url: advanced_order_pizza_bot.html
}
---

## Function 노드 를 활용하여 변수값을 가공하기
대화흐름에서 사용하기 위해 만든 내부변수의 경우 Slot 노드에서 사용자가 입력한 값이나 API 노드 에서 받아온 값을 사용할 수 있다는 것을 배웠습니다. 하지만 보다 자연스러운 대화를 위해서는 값을 그대로 쓰기 보다는 조금 가공하여 사용해야 할 때도 있죠. <br/>
피자주문하는 시나리오에서 피자가격을 주는 외부시스템의 경우 가격을 정수 형태로 보내줍니다. <br/>
그러나 사용자에게 가격을 보여줄때는 천단위에 쉼표를 넣어서 보여주고 싶은 경우에는 어떻게 해야 할까요? <br/>
아래 예제를 통해 살펴 보도록 하겠습니다.

### Function 노드 를 대화흐름 창에서 설정하기
계속해서 기존에 만들던 피자주문 시나리오에 [Function Node](/chatflow_function.html#function-%EB%85%B8%EB%93%9C)를 추가합니다. <br/>
<br/>

1) Function 노드를 클릭하여 작업공간에 추가해 주세요.

2) Api 노드 와 Split 노드 사이에 Function 노드를 위치 시키고 앞뒤 노드와 연결해 주세요. <br/>
기존에 연결된 선의 경우 마우스로 선을 클릭하고 선이 붉은색으로 하이라이트된 후 키보드의 delete 키를 누르면 삭제됩니다.

{% include image.html file="tutorial/basic_function_node1.gif"  caption="Function 노드 생성하기1" %}

### Function 노드 상세정보 설정하기

1) Function 노드를 더블 클릭하여 상세패널을 엽니다. 개발자들이 사용할 법한 텍스트 입력 창이 나옵니다. 

2) Javascript 문법을 사용하여 프로그램을 작성하시면 원하는대로 값을 변경 할수 있습니다. Function 노드 에서 대화흐름내 내부 변수명을 기입하면 변수에 값을 넣고 빼고 할 수 있습니다. 튜토리얼에서는 Api 노드 를 통해 가져온 피자가격 변수를 가져오도록 하겠습니다.

3) Javascript 의 toString() 과 replace() 함수와 정규식을 이용해 천단위에 쉼표를 넣은 후 피자가격 변수에 가공된 값을 넣도록 합니다. (아래 내용을 복사해서 붙여넣으면 됩니다.)

```js
피자가격 = 피자가격.toString().replace(/(\d)(?=(\d\d\d)+(?!\d))/g, "$1,");
````

5) ✔반영확인 버튼을 클릭해 상세화면을 닫습니다. 그리고 [변경내용 저장]도 클릭해서 닫아줍니다.

{% include image.html file="tutorial/basic_function_node2.gif"  caption="Function 노드 생성하기2" %}

### Function 노드 테스트
1) “대화흐름 저장” 버턴을 클릭한 후 우측의 테스트 패널에서 테스트를 해보세요. “피자 주문해줘”라고 입력 후 피자메뉴 선택 하면 <br/>
피자가격 변수의 값이 12,000 으로 변경된 것을 확인 할 수 있습니다.

{% include image.html file="tutorial/basic_function_node1.png"  caption="Function 노드 생성하기2" %}




{% include bottom.html %}