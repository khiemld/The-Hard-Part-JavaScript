# Execution Context - Call stack

## 1. The definition

- JavaScript is a single thread language, meaning it just execute one process at a time
- Execution Context (EC): enviroment where JS code is executed. When JS is executed, a EC is created
- Execution context has 3 components: 
  - Variable enviroment: contains variable and function declaration defined with the context 
  - Lexical enviroment: similar to variable enviroment, but also include the lexical scope chain. It determined the visibility and accessibility of variable and function base on their nested structure. It allow inner function access variable from their outer function. 
  - Value: Determined how the function is call and vary depending on the context with the function is invoked
- Execution context has 2 phases: the creation phase and the execution phase.

## 2. Call stack

- Used to manage Execution Context
- When is the code executed, it create Execution Context for each function call or block of code. These EC are stacked in a specific order —> Call stack
- CallStack follow the LIFO structure, when function is called, the EC of this is pop out the stack and return the previous EC. Finally, it return to the global execution context.

## 3. Example

```js
function multiplyBy2(inputNumber) {
  const result = inputNumber * 2;
  return result;
}

const output = multiplyBy2(num);
const newOutput = multiplyBy2(10);
```

#### Explain

![alt](./img/PrincipleJS%403x.png)

1. In the global Memory, we define function multiplyBy2 with parameter is inputNumber.
2. Then, we declare const output and call function multiplyBy2.
  - 2.1 When multiplyBy2 is called, a Execution Context is created. And it is pushed onto Call stack.
  - 2.2 In local memory of Execution Context, we have input is num set value of 3 and declare variable 'result'. Let's look execution phases, it is process operation 'num\*2\' is '3\*2'. And assign 6 to variable 'result. And return out 'result' to variable 'output'.
  - 2.3 The Call stack pop out the execution context. At the same time, the execution context is deleted. And we back to the Global Execution Context
3. Back to the global memory, we continue to declare const newOutput and call function multiplyBy2. (The thread of execution is same as above).
