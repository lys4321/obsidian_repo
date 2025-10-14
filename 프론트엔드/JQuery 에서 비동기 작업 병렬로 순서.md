function sequentialExecutionFrame(procceedMethods(#1)) {
	$("#loading").show();
	return(#2) $.when( ...(#3)procceedMethods.map(fn => fn())(#4) )
		.fail(function() {
			alert('오류가 발생하였습니다.');
			$('#containDiv div').empty();
		}).always(function() {
			$("#loading").hide();
		});
}
sequentialExecutionFrame([
	 (#5)function1
	,(#6)() => function2(parameter)
	,function3
	,() => function4(parameter)
	...
]);
#1 : 순서지정 함수에서 매개변수를 위한 함수들의 배열을 입력 
#2 : 만약 해당 코드에서 끝이 난다면 상관없지만 
	이후에도 추가로 순서 지정 작업이 필요하다면 Promise를 반환해줘야한다.
#3 : ... 는 전개연산자
#4 : 매개변수로 받는 모든 함수가 작동하는데 매개변수가 필요로 없다면
		...procceedMethods로 설정해도 되지만 있다면 람다식을 사용해 
			들어온 매개변수를 이용할 수 있도록 해야한다.
#5 : 위에서 fn => fn()로 지정해서 함수명만 입력 시 함수명()로 인식되기 때문에 
		함수명만 입력
#6 : 매개변수가 있는 함수의 경우 작성법