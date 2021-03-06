# 동기(sync)와 비동기(async)의 차이

동기는 반드시 코드를 순차적으로 실행하는 것이고, 비동기는 전달받은 콜백을 나중에(이벤트 발생 시 등등) 실행하는 것이다.   
   
동기는 앞에 있는 코드의 실행이 완료되어야 다음 코드를 실행하므로, 실행 순서를 보장받을 수 있다는 장점이 있으나, 순차적으로 실행하고자 하는 코드의 실행 시간이 매우 길어질 경우, 브라우저가 멈춘 것으로 오인될 수도 있다.   
   
비동기는 콜백 함수를 파라미터로 받은 다음, 실행 즉시 그 다음 코드를 실행한다. 콜백은 비동기 작업이 완료되고 콜 스택이 비었을 때 실행된다. 실행 순서는 보장되지 않으나, 웹 서버와 통신(데이터를 받아오거나 DB 쿼리를 실행)하는 등 매우 무거운 작업을 브라우저 멈춤 없이 진행할 수 있다.