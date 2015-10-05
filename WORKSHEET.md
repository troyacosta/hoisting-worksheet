# JavaScript Hoisting Worksheet

## Instructions
1. Review each code snippet below.
2. Fill in what will be output to the console.
3. Run the code to see if you were correct.
4. Describe why the code behaved as it did.
5. Re-write the code snippet to maintain the same output, but to avoid hoisting.

```js
var myvar = 'my value'; 
  
(function() { 
	console.log(myvar);
	var myvar = 'local value'; 
})();
```

> output:
>-Undefined
>-
>-
> why?
>-Because the declaration 'var myvar' will be hoisted to the top 
>-of the function but it will not bring the value of the varible with it.
>-
>-
>-
>-
> rewrite without hoisting
>-(function() {
	var myvar
	console.log(myvar);
	myvar = 'local value';
})()
>-
>-

```js
var flag = true; 
  
function test() {
	if(flag) {
		var flag = false;
		console.log('Switch flag from true to false');
	}
	else {
		flag = true;
		console.log('Switch flag from false to true');
	}
}
test();
```

> output:
>-'Switch flag from false to true'
>-
>-
> why?
>-Because 'var flag' will be hoisted to the top of the function and will then evaluate to 
>-undefined, which is a false. So then the if statement will be ignored and the else statement will run.
>-
>-
>-
>-
> rewrite without hoisting
>-function test() {
	var flag
>-		if(flag) {
>-			flag = false;
>-			console.log('Switch flag from true to false');
>-		}
>-		else {
		flag = true;
		console.log('Switch flag from false to true');
	}
}
test();
>-
>-
>-
>-
>-
>-


```js
var message = 'Hello world'; 
  
function saySomething() {
	console.log(message);
	var message = 'Foo bar';
}
saySomething();
```

> output:
>-undefined
>-
>-
> why?
>-Because 'var message' will be hoisted to the top of the function but will
>-not have its definition, therefor it will be undefined when logged.
>-
>-
>-
>-
> rewrite without hoisting
>-
>-function saySomething() {
	var message
	console.log(message);
	message = 'Foo bar';
}
saySomething();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-

```js
var message = 'Hello world'; 
  
function saySomething() {
	console.log(message);
	message = 'Foo bar';
}
saySomething();
```

> output:
>-'Hello world'
>-
>-
> why?
>-Because 'message' doesn't get redefined until after the console.log statement is executed.
>-And 'message = Foo bar' isn't hoisted since it's not a newly declared varible.
>-
>-
>-
>-


```js
function test() {
	console.log(a);
	console.log(foo());

	var a = 1;
	function foo() {
		return 2;
	}
}
 
test();
```

> output:
>-undefined
>-2
>-
> why?
>-Because 'var a' will be hoisted to the top where it will then evaluate to 'undefined'.
>-2 will then be logged because the function foo will be hoisted to the top and therefor
>-be available to be executed in the console.log statement.
>-
>-
>-
> rewrite without hoisting
>-function test() {
	var a
	function foo() {
		return 2;
	}
	console.log(a);
	console.log(foo());
	a = 1;
}
 
test();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-

```js
(function() {
	console.log(bar);
	foo();

	function foo() {
		console.log('aloha');
	}

	var bar = 1;
	baz = 2;
})();
```

> output:
>-undefined
>-aloha
>-
> why?
>-Because 'var bar' will be hoisted to the top which will then evaluate to undefined when logged.
>-aloha will be logged because the function foo will be hoisted to the top making it available for the 
>-console.log statement.
>-baz doesn't do shit.
>-
>-
> rewrite without hoisting
>-(function() {
	var bar
	function foo() {
		console.log('aloha');
	}
	console.log(bar);
	foo();

	bar = 1;
	baz = 2;
})();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-

```js
var run = false;

function fancy(arg1, arg2) {
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}

	function run() {
		console.log('Will I run?');
	}
}
fancy();
```

> output:
>-I can run
>-
>-
> why?
>-Because the function run will be hoisted to the top, then the if statement will be evaluatung 
>-the run function, which evaluated to true, therefor the statement inside the 'if' will be executed.
>-
>-
>-
>-
> rewrite without hoisting
>-function fancy(arg1, arg2) {
	function run() {
		console.log('Will I run?');
	}
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}
}
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-

```js
var run = false;

function fancy(arg1, arg2) {
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}

	var run = function() {
		console.log('Will I run?');
	}
}
fancy();
```

> output:
>-I can't run
>-
>-
> why?
>-Because 'var run' will be hoisted to the top which will then evaluate to undefined. Since undefined
>-evaluates to a falsey value the if statement will be ignored leaving the else statement to be executed.
>-
>-
>-
>-
> rewrite without hoisting
>-
>-function fancy(arg1, arg2) {
 	var run
	if(run) {
		console.log('I can run');
	}
	else {
		console.log('I can\'t run');
	}

	run = function() {
		console.log('Will I run?');
	}
}
fancy();
>-
>-
>-
>-
>-
>-
>-
>-
>-
>-