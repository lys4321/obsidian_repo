1. 비동기 작업 하나에서 순서지정
	(#1)fetch('url', {
		method : --- ,
		header : { ... } ,
		body : 요청에 필요한 값들
	})
	.then( response => response.json() )  (#2)
	.then( data => { 처리 } ) 
	...
	.catch( error => { 에러처리 } )
	#1 : fetch는 Promise 반환
	#2 : then은 서로 체이닝(연결)이 가능하여 위의 then부터 순차적으로 실행하고
		다음  then 에게 반환값을 줄 수 있음

2. 여러 비동기 작업 병렬 처리 순서 지정
	 (#1)Promise.all([
	  (#2)
	  function1() ,
	  function2() ,
	  ...
	 ])
	 .then((#3)[ response1, response2, ... ])
	 .catch(erorr => {  에러처리 });
   #1 : 여러 비동기 작업을 병럴로 순서처리하기 위해 사용
   #2 : 사용되는 함수들은 각각 Promise를 반환해야함
   #3 : 각 함수들의 응답을 받아 모두 성공이면 처리시작