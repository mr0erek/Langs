All code snippets explained in **JavaScript Full Course | JavaScript - Learn Everything** by Sheryians Coding School organized by section with timestamps.

---

[![JavaScript Full Course – Sheryians Coding School](https://img.youtube.com/vi/a-wVHL0lpb0/maxresdefault.jpg)](https://www.youtube.com/watch?v=a-wVHL0lpb0)

> Click the thumbnail to open the full video. Every timestamp below jumps to that exact moment on YouTube.



---

## Setup & Prerequisites

Linking JavaScript to an HTML file [`00:03:12`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=192s) [`00:13:59`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=839s):

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Document</title>
</head>
<body>
  <script src="script.js"></script>
</body>
</html>

```

---

## 1. Variables & Declarations

### `var`, `let`, `const`, Declaration & Initialization [`00:17:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=1025s) [`00:21:41`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=1301s)

```js
var a;              // Declaration
var a = 12;         // Declaration & Initialization
let b;
let b = 12;
const c = 12;       // Must be initialized at declaration

// Redeclaration: allowed with var, error with let [00:26:41]
var x = 12;
var x = 13;         // No error

let y = 12;
// let y = 13;      // SyntaxError: Identifier 'y' has already been declared

// Reassignment with const throws an error [00:30:12]
const dulha = "Lab";
const dulhan = "Laby";
// dulha = "Haramzada"; // TypeError: Assignment to constant variable

```

> ⏱ In this snippet: [`00:26:41`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=1601s) · [`00:30:12`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=1812s)

### Scope (Global, Block, Functional) [`00:35:29`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=2129s) [`00:38:49`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=2329s)

```js
var globalVar = 12; // Global scope

{
  let blockScoped = 12; // Block scoped (respects curly braces)
  var leaksOut = 13;    // Function scoped (ignores block)
}

function abcd() {
  if (true) {
    var a = 12;     // Accessible anywhere inside abcd()
    let b = 15;     // Accessible only inside this if block
  }
}

```

### Reassignment vs. Redeclaration [`00:40:53`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=2453s)

```js
var a = 12;
a = 32;             // Reassignment (allowed)
var a = 233;        // Redeclaration (allowed with var)

let b = 12;
b = 32;             // Reassignment (allowed)
// let b = 433;     // Redeclaration (not allowed with let)

```

### Temporal Dead Zone (TDZ) & Hoisting [`00:45:12`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=2712s) [`00:52:57`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=3177s)

```js
// TDZ with let [00:45:12]
// console.log(a);  // ReferenceError: Cannot access 'a' before initialization
let a = 12;

// Hoisting with var [00:52:57]
console.log(b);     // undefined
var b = 12;

// Behind the scenes for var:
// var b = undefined;
// console.log(b);
// b = 12;

```

### Practice Questions & Common Confusions [`00:59:16`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=3556s) [`01:03:56`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=3836s)

```js
// Q1: var hoisting -> undefined [00:59:16]
console.log(nm);
var nm = "Harsh";

// Q2: let TDZ -> ReferenceError [01:00:18]
// console.log(age);
// let age = 25;

// Q3: var ignores block scope -> 2 [01:01:21]
var x = 1;
{
  var x = 2;
}
console.log(x);     // 2

// Q4: let respects block scope -> Inside: 20, Outside: 10 [01:02:16]
let a = 10;
{
  let a = 20;
  console.log("Inside:", a);  // 20
}
console.log("Outside:", a);   // 10

// Confusion 1: var leaks out of if block, let does not [01:03:56]
if (true) {
  var a = 1;
  let b = 2;
}
console.log(a);     // 1
// console.log(b);  // ReferenceError

// Confusion 2: const allows mutating object properties, not reassignment [01:05:26]
const person = { name: "Harsh" };
person.name = "Sharma"; // Allowed (updating property)
// person = {};         // TypeError (reassignment not allowed)

```

> ⏱ In this snippet: [`01:00:18`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=3618s) · [`01:01:21`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=3681s) · [`01:02:16`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=3736s) · [`01:05:26`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=3926s)

---

## 2. Data Types & Type System

### Primitives vs. Reference Types [`01:14:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=4445s) [`01:17:16`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=4636s)

```js
// Primitive copy (independent copy)
let a = 12;
let b = a;
a = a + 2;          // a is 14, b is still 12

// Reference copy (shared reference) [01:17:16]
let arr1 = [1, 2, 3];
let arr2 = arr1;
arr2.pop();         // Both arr1 and arr2 become [1, 2]

// Same for objects [01:38:26]
let obj1 = { name: "harsh" };
let obj2 = obj1;
obj2.name = "harshita"; // Both obj1.name and obj2.name become "harshita"

```

> ⏱ In this snippet: [`01:38:26`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=5906s)

### All Primitive Types (`string`, `number`, `boolean`, `null`, `undefined`, `Symbol`, `BigInt`) [`01:20:26`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=4826s) [`01:31:01`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=5461s) [`01:34:06`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=5646s)

```js
// Strings
let s1 = 'harsh';
let s2 = "harsh";
let s3 = `harsh`; // backticks ` can evaluates variables into strings itself
const price = 100;
const tax = 18;
const total = `Total amount: ₹${price + tax}`; 
// Output: "Total amount: ₹118"

// Numbers (integers & decimals are both 'number')
let n1 = 12;
let n2 = 12.3;

// Booleans
let flag1 = true;
let flag2 = false;

// null (intentionally empty) vs undefined (default unassigned) [01:22:43]
let selectedStudents = null;
let unassigned;     // undefined

// Symbol (unique immutable identifier) [01:31:01]
let u1 = Symbol("uid");
let u2 = Symbol("uid");
console.log(u1 === u2); // false

let obj = {
  uid: 1,
  name: "harsh",
  age: 12,
  email: "test@test.com",
};
obj[u1] = "001";    // Adds a unique Symbol property without overwriting uid

// BigInt [01:34:06]
let max = Number.MAX_SAFE_INTEGER; // 9007199254740991
let big = 9007199254740991n;
big + 3n;           // 9007199254740994n

```

> ⏱ In this snippet: [`01:22:43`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=4963s)

### Dynamic Typing, `typeof` Quirks, Type Coercion & Truthy/Falsy [`01:41:59`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=6119s) [`01:44:30`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=6270s) [`01:50:55`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=6655s) [`01:55:25`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=6925s)

***Quirks:*** *unexpected, weird, or counter-intuitive behaviors in a language that defy normal logic* 
> ***Inshort*** :
*Quirks matlab kisi language ke woh ajeeb, tedhe-medhe or unexpected nakhre, jo normal logic ke hisaab se hone hi nahi chahiye, par language mein hote hain!*

```js
// Dynamic typing [01:41:59]
let a = 12;
a = true;
a = "harsh";
a = [];
a = null;
a = undefined;

// typeof & JS quirks [01:44:30]
typeof 12;          // "number"
typeof "harsh";     // "string"
typeof null;        // "object" (quirk)
typeof NaN;         // "number" (quirk: failed number operation, e.g. 2 * "harsh")
NaN === NaN;        // false
0.1 + 0.2;          // 0.30000000000000004
[] + [];            // ""
1 == "1";           // true
1 === "1";          // false

// Type coercion [01:50:55]
"5" + 1;            // "51" (concatenation)
"5" - 1;            // 4 (subtraction converts string to number)

// Falsy values: 0, false, "", null, undefined, NaN, document.all [01:55:25]
// Check truthiness with !!
!!0;                // false
!!"";               // false
!!NaN;              // false
!!null;             // false
!!undefined;        // false
!!document.all;     // false
!!-1;               // true (everything else is truthy)

// Practice outputs [01:58:28]
true + false;       // 1
null + 1;           // 1
"5" + 5;            // "55"
!!undefined;        // false

```

> ⏱ In this snippet: [`01:58:28`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=7108s)

---

## 3. Operators

### Arithmetic, Comparison, Assignment, Logical, Unary & Ternary [`02:06:28`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=7588s) [`02:16:46`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=8206s) [`02:24:22`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=8662s) [`02:29:01`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=8941s)

```js
// Arithmetic [02:06:28]
1 + 2;              // 3
"ha" + "rsh";       // "harsh"
12 - 2;             // 10
12 / 6;             // 2
12 * 2;             // 24
12 % 5;             // 2 (modulus / remainder)
2 ** 3;             // 8 (exponentiation)

// Comparison [02:10:40]
12 == 13;           // false
12 == "12";         // true (loose)
12 === "12";        // false (strict)
12 != 13;           // true
12 != "12";         // false (loose)
12 !== "12";        // true (strict)
12 > 11;            // true
22 <= 22;           // true
32 >= 32;           // true

// Assignment [02:16:46]
let a = 12;
a += 3;             // 15
a -= 11;            // 4
a *= 2;             // 8
a /= 2;             // 4
a %= 3;             // 1

// Logical [02:19:00]
true && true;       // true
12 > 13 && 13 > 10; // false
12 > 13 || 13 > 10; // true
!false;             // true
!!12;               // true

// Unary [02:24:22]
+"5";               // 5 (converts numeric string to number)
+"harsh";           // NaN
-5;                 // -5
!12;                // false

// Pre vs Post Increment / Decrement [02:25:54]
let n = 12;
++n;                // 13 (pre-increment: updates immediately)
n++;                // 13 (post-increment: uses old value, then updates to 14)

let v = 2;
v++ + v;            // 2 + 3 = 5

// Ternary [02:29:01]
12 > 13 ? console.log("true") : console.log("false");

// typeof vs instanceof [02:30:56]
typeof [];          // "object"
let arr = [];
arr instanceof Array;   // true
let obj = {};
obj instanceof Object;  // true
obj instanceof Array;   // false
let num = 12;
num instanceof Number;  // false (instanceof works on reference types)

```

> ⏱ In this snippet: [`02:10:40`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=7840s) · [`02:19:00`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=8340s) · [`02:25:54`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=8754s) · [`02:30:56`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=9056s)

### Practice Questions [`02:35:07`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=9307s) [`02:41:15`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=9675s)

```js
// Logical & Conditional practice [02:35:07]
let x = 10, y = 20;
if (x > 5 && y < 25) {
  console.log("A"); // "A"
}

let isAdmin = true, isLoggedIn = false;
if (isAdmin || isLoggedIn) {
  console.log("Access granted"); // "Access granted"
}

let temp = 35;
if (!(temp < 30)) {
  console.log("Hot"); // "Hot"
}

let a = 0;
if (a) {
  console.log("Truthy");
} else {
  console.log("Falsy"); // "Falsy"
}

// Chained Ternary: Grades [02:37:47]
let score = 78;
let grade = score >= 90 ? "A" : score >= 75 ? "B" : score >= 60 ? "C" : "Fail";
console.log(grade); // "B"

// Chained Ternary: Points [02:39:17]
let points = 120;
let status = points > 100 ? "Gold" : points > 50 ? "Silver" : "Bronze";
console.log(status); // "Gold"

// Ternary: Access [02:40:24]
let loggedIn = true, hasToken = false;
let access = loggedIn && hasToken ? "Allow" : "Deny";
console.log(access); // "Deny"

// Increment / Decrement Puzzles [02:41:15]
// 1.
let p1 = 5;
p1++;
console.log(p1);    // 6

// 2.
let p2 = 7;
++p2;
console.log(p2);    // 8

// 3.
let x3 = 3;
let y3 = x3++;
console.log(x3, y3); // 4, 3

// 4.
let p4 = 4;
let q4 = ++p4;
console.log(p4, q4); // 5, 5

// 5.
let m = 10;
console.log(m--);   // 10
console.log(m);     // 9

// 6.
let n6 = 5;
let result = n6++ + ++n6;
console.log(result); // 5 + 7 = 12

// 7.
let likes = 100;
function likePost() {
  return ++likes;
}
console.log(likePost()); // 101
console.log(likes);      // 101

// 8.
let count = 5;
if (count-- === 5) {
  console.log("Matched"); // "Matched"
} else {
  console.log("Not matched");
}

```

> ⏱ In this snippet: [`02:37:47`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=9467s) · [`02:39:17`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=9557s) · [`02:40:24`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=9624s)

---

## 4. Control Flow

### `if`, `else if`, `else`, `switch-case` & Early Return [`02:53:34`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=10414s) [`02:57:38`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=10658s) [`03:00:28`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=10828s)

```js
// if / else if / else [02:55:46]
if (loggedIn && admin) {
  // admin view
} else if (loggedIn) {
  // user view
} else {
  // login prompt
}

// switch-case [02:57:38]
switch (1) {
  case 1:
    console.log("case 1");
    break; // Missing break causes fall-through into case 2 [03:19:38]
  case 2:
    console.log("case 2");
    break;
  case 3:
    console.log("case 3");
    break;
  default:
    console.log("default");
}

// Early Return Pattern [03:02:46]
function getVal(val) {
  if (val < 25) return "D";
  else if (val < 50) return "C";
  else if (val < 75) return "B";
  else return "A";
}
console.log(getVal(76)); // "A"

```

> ⏱ In this snippet: [`02:55:46`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=10546s) · [`03:19:38`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=11978s) · [`03:02:46`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=10966s)

### Practice: `getGrade(score)` & Rock-Paper-Scissors [`03:05:17`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=11117s) [`03:13:09`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=11589s)

```js
// getGrade using Early Return [03:10:19]
function getGrade(score) {
  if (score >= 90 && score <= 100) return "A";
  if (score >= 80 && score <= 89) return "B";
  if (score >= 70 && score <= 79) return "C";
  if (score >= 60 && score <= 69) return "D";
  if (score >= 33 && score <= 59) return "E";
  if (score >= 0 && score <= 32) return "Fail";
  return "Invalid marks";
}
console.log(getGrade(54)); // "E"

// Rock-Paper-Scissors Logic [03:16:17]
function rps(user, computer) {
  if (user === computer) return "draw";

  if (user === "rock" && computer === "scissor") return "user";
  if (user === "scissor" && computer === "paper") return "user";
  if (user === "paper" && computer === "rock") return "user";

  return "computer";
}
console.log(rps("scissor", "rock")); // "computer"

```

> ⏱ In this snippet: [`03:10:19`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=11419s) · [`03:16:17`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=11777s)

---

## 5. Loops

### `for`, `while`, `do-while`, `break` & `continue` [`03:39:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=13145s) [`03:45:35`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=13535s) [`03:47:10`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=13630s) [`03:49:45`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=13785s)

```js
// for loop (1 to 100) [03:39:05]
for (let i = 1; i < 101; i++) {
  console.log(i);
}

// while loop (1 to 31) [03:45:35]
let i = 1;
while (i < 32) {
  console.log(i);
  i++;
}

// do-while loop (runs at least once even if condition is false) [03:47:55]
let j = 12;
do {
  console.log(j);   // Prints 12 once
  j++;
} while (j < 2);

// break (stops loop at 32) [03:49:45]
for (let i = 1; i < 201; i++) {
  console.log(i);
  if (i === 32) {
    break;
  }
}

// continue (skips 32) [03:51:23]
for (let i = 1; i < 201; i++) {
  if (i === 32) {
    continue;
  }
  console.log(i);
}

```

> ⏱ In this snippet: [`03:47:55`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=13675s) · [`03:51:23`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=13883s)

### Loop Practice Questions [`03:54:04`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=14044s) – [`04:36:40`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=16600s)

```js
// Q1: Print 1 to 10 using for loop [03:54:04]
for (let i = 1; i < 11; i++) {
  console.log(i);
}

// Q2: Print 10 to 1 using while loop [03:59:22]
let k = 10;
while (k > 0) {
  console.log(k);
  k--;
}

// Q3: Print even numbers 1 to 20 [04:02:33]
for (let i = 1; i < 21; i++) {
  if (i % 2 === 0) {
    console.log(i);
  }
}

// Q4: Print odd numbers 1 to 15 using while [04:04:47]
let m = 1;
while (m < 16) {
  if (m % 2 === 1) {
    console.log(m);
  }
  m++;
}

// Q5: Multiplication table of 5 [04:09:31]
for (let i = 1; i < 11; i++) {
  console.log(`5 * ${i} = ${5 * i}`);
}

// Q6: Sum of numbers 1 to 100 [04:11:18]
let sum = 0;
for (let i = 1; i < 101; i++) {
  sum = sum + i;
}
console.log(sum);   // 5050

// Q7: Numbers 1 to 50 divisible by 3 [04:15:59]
for (let i = 1; i < 51; i++) {
  if (i % 3 === 0) {
    console.log(i);
  }
}

// Q8: Prompt user for number and print even/odd from 1 to N [04:17:13]
let val = prompt("give a number");
for (let i = 1; i <= val; i++) {
  if (i % 2 === 0) {
    console.log(`${i} is even`);
  } else {
    console.log(`${i} is odd`);
  }
}

// Q9: Numbers 1 to 100 divisible by both 3 and 5 [04:19:44]
for (let i = 1; i < 101; i++) {
  if (i % 3 === 0 && i % 5 === 0) {
    console.log(i);
  }
}

// Break & Continue Q1: Stop at first multiple of 7 [04:21:18]
for (let i = 1; i < 101; i++) {
  console.log(i);
  if (i % 7 === 0) {
    break;
  }
}

// Break & Continue Q2: Skip multiples of 3 (1 to 20) [04:22:51]
for (let i = 1; i < 21; i++) {
  if (i % 3 === 0) continue;
  console.log(i);
}

// Break & Continue Q3: Print first 5 odd numbers only [04:24:16]
let count = 0;
for (let i = 1; i < 101; i++) {
  if (i % 2 === 1) {
    count++;
    console.log(i);
  }
  if (count === 5) break;
}

// Bonus: Count digits in a number [04:36:40]
let num = 12345;
let digitCount = 0;
while (num > 0) {
  num = Math.floor(num / 10);
  digitCount++;
}
console.log(digitCount); // 5

```

> ⏱ In this snippet: [`03:59:22`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=14362s) · [`04:02:33`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=14553s) · [`04:04:47`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=14687s) · [`04:09:31`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=14971s) · [`04:11:18`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=15078s) · [`04:15:59`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=15359s) · [`04:17:13`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=15433s) · [`04:19:44`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=15584s) · [`04:21:18`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=15678s) · [`04:22:51`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=15771s) · [`04:24:16`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=15856s)

---

## 6. Functions

### Declaration, Expression, Arrow, Parameters, Default & Rest [`04:47:56`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=17276s) [`04:54:31`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=17671s) [`05:04:45`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=18285s) [`05:09:26`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=18566s)

```js
// Function Declaration (Statement) [04:47:56]
function lolo() {
  console.log("happy new year");
}
lolo();

// Function Expression [04:50:17]
let fnc = function () {
  console.log("hey");
};
fnc();

// Fat Arrow Function [04:54:31]
let arrowFnc = () => {
  console.log("hey");
};
arrowFnc();

// Parameters & Arguments [04:57:10]
function dance(v1) {
  console.log(`${v1} naach raha hai`);
}
dance("ghoda");
dance("hiran");

// Default Parameters [05:04:45]
function add(v1 = 0, v2 = 0) {
  console.log(v1 + v2);
}
add();              // 0
add(1, 2);          // 3

// Rest Operator (...) in Parameters [05:09:26]
function abcd(a, b, c, ...val) {
  console.log(a, b, c, val);
}
abcd(1, 2, 3, 4, 5, 6); // 1 2 3 [4, 5, 6]

// Return value [05:12:01]
function calc(v) {
  return 12 + v;
}
let res = calc(23); // 35

```

> ⏱ In this snippet: [`04:50:17`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=17417s) · [`04:57:10`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=17830s) · [`05:12:01`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=18721s)

### First-Class, Higher-Order (HOF), Pure vs. Impure, Closures, Lexical Scope, IIFE & Hoisting [`05:17:29`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=19049s) – [`05:32:02`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=19922s)

```js
// First-Class & Higher-Order Function (accepting a function) [05:17:29]
function abcd(val) {
  val();
}
abcd(function () {
  console.log("hey");
});

// Higher-Order Function (returning a function) [05:20:31]
function outerFn() {
  return function () {
    console.log("hey");
  };
}
outerFn()();

// Pure vs Impure Functions [05:23:05]
let a = 12;
function pureFn() {
  console.log("hehehe"); // Does not modify external state
}
function impureFn() {
  a++;                   // Modifies external variable 'a'
}

// Closure [05:24:54]
function makeClosure() {
  let a = 12;
  return function () {
    console.log(a);      // Uses parent's variable
  };
}

// Lexical Scoping [05:26:19]
function level1() {
  let a = 12;
  function level2() {
    let b = 13;
    function level3() {
      let c = 14;
    }
  }
}

// IIFE (Immediately Invoked Function Expression) [05:29:09]
(function () {
  console.log("runs immediately");
})();

// Hoisting Difference [05:31:00]
sayHi();                 // Works (Declaration is hoisted)
function sayHi() {
  console.log("hey");
}

// sayBye();             // ReferenceError (Expression is NOT hoisted)
let sayBye = function () {
  console.log("bye");
};

```

> ⏱ In this snippet: [`05:20:31`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=19231s) · [`05:23:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=19385s) · [`05:24:54`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=19494s) · [`05:26:19`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=19579s) · [`05:29:09`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=19749s) · [`05:31:00`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=19860s)

### Function Practice & Mini-Projects [`05:35:17`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=20117s) – [`06:12:35`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=22355s)

```js
// Convert to Arrow Function [05:35:17]
let multiply = (a, b) => {
  return a * b;
};

// Rest Parameter Score Total [05:38:11]
function getScore(...scores) {
  let total = 0;
  scores.forEach(function (val) {
    total = total + val;
  });
  return total;
}
console.log(getScore(10, 12, 14, 18)); // 54

// Early Return Fix [05:41:40]
function checkAge(age) {
  if (age < 18) return "Too young";
  return "Allowed";
}
console.log(checkAge(23)); // "Allowed"

// Convert to Pure Function [05:47:30]
let total = 0;
function addToTotal(num) {
  let newTotal = total;
  newTotal += num;
  return newTotal;
}

// Closure Counter [05:49:15] [06:07:02]
function counter() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}
let c = counter();
console.log(c());   // 1
console.log(c());   // 2
let d = counter();
console.log(d());   // 1 (separate closure state)

// IIFE with Private Variable (Getter/Setter Module) [05:53:50]
let shery = (function () {
  let score = 0;
  return {
    getScore: function () {
      console.log(score);
    },
    setScore: function (val) {
      score = val;
    },
  };
})();
shery.getScore();   // 0
shery.setScore(20);
shery.getScore();   // 20

// BMI Calculator [05:57:35]
function bmi(weight, height) {
  return weight / (height * height);
}
console.log(bmi(69, 1.7).toFixed(2)); // "23.88"

// Reusable Discount Calculator (HOF / Closure) [06:01:27]
function discountCalculator(discount) {
  return function (price) {
    return price - price * (discount / 100);
  };
}
let ten = discountCalculator(10);
let twenty = discountCalculator(20);
console.log(ten(1200));    // 1080
console.log(twenty(1200)); // 960

// Pure Transform Function [06:10:50]
function double(val) {
  return val * 2;
}
console.log(double(5)); // 10

// IIFE Isolating Variables [06:11:42]
(function () {
  const password = "secret password";
  console.log(password);
})();
// console.log(password); // ReferenceError: password is not defined

```

> ⏱ In this snippet: [`05:38:11`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=20291s) · [`05:41:40`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=20500s) · [`05:47:30`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=20850s) · [`05:49:15`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=20955s) · [`06:07:02`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=22022s) · [`05:53:50`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=21230s) · [`05:57:35`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=21455s) · [`06:01:27`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=21687s) · [`06:10:50`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=22250s) · [`06:11:42`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=22302s)

---

## 7. Arrays

### Creation, Access, Modification & Mutating/Non-Mutating Methods [`06:19:36`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=22776s) – [`06:32:21`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=23541s)

```js
// Create & Access [06:19:36]
let marks = [10, 40, 52, 37, 92];
marks[0];           // 10
marks[3];           // 37
marks[50];          // undefined

let arrAlt = new Array(); // Alternate creation [06:23:05]

// Modify [06:23:45]
let arr = [1, 2, 3, 4];
arr[2] = 12;        // [1, 2, 12, 4]

// Core Methods [06:25:16]
let nums = [1, 2, 3, 4, 5];
nums.push(7000);    // Adds to end
nums.pop();         // Removes from end
nums.shift();       // Removes from start
nums.unshift(0);    // Adds to start
nums.splice(2, 1);  // Removes 1 element starting at index 2 (mutates original)

let sliced = nums.slice(0, 3); // Returns new copy from index 0 up to (not including) 3
nums.reverse();     // Reverses original array in place

// Numeric Sort (always pass compare function) [06:31:08]
let unsorted = [11, 62, 3, 4, 25];
let asc = unsorted.sort(function (a, b) {
  return a - b;     // Ascending: [3, 4, 11, 25, 62]
});
let desc = unsorted.sort(function (a, b) {
  return b - a;     // Descending: [62, 25, 11, 4, 3]
});

```

> ⏱ In this snippet: [`06:23:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=22985s) · [`06:23:45`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=23025s) · [`06:25:16`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=23116s) · [`06:31:08`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=23468s)

### Iteration & Higher-Order Array Methods [`06:34:12`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=23652s) – [`06:51:36`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=24696s)

```js
let arr = [11, 62, 3, 4, 25];

// forEach [06:34:12]
arr.forEach(function (val) {
  console.log(val + 5);
});

// map (returns new array of same length) [06:36:10]
let mapped = arr.map(function (val) {
  if (val > 10) return val; // returns undefined for items not matching
});

// filter (returns new array with items where callback returns true) [06:41:19]
let list = [1, 2, 3, 4, 5, 6, 7, 8];
let filtered = list.filter(function (val) {
  if (val > 4) return true;
}); // [5, 6, 7, 8]

// reduce (reduces array to a single value) [06:43:35]
let nums = [1, 2, 3, 4, 5, 6];
let total = nums.reduce(function (accumulator, val) {
  return accumulator + val;
}, 0); // 21

// find (returns first matching element) [06:47:57]
let objs = [
  { id: 1, key: 1 },
  { id: 2, key: 2 },
  { id: 3, key: 1 },
];
let found = objs.find(function (val) {
  return val.key === 1;
}); // { id: 1, key: 1 }

// some (true if at least one matches) [06:50:05]
let scores = [10, 30, 32, 90];
let anyHigh = scores.some(function (val) {
  return val > 85;
}); // true

// every (true only if all match) [06:51:04]
let allAbove5 = scores.every(function (val) {
  return val > 5;
}); // true

```

> ⏱ In this snippet: [`06:36:10`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=23770s) · [`06:41:19`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=24079s) · [`06:43:35`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=24215s) · [`06:47:57`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=24477s) · [`06:50:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=24605s) · [`06:51:04`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=24664s)

### Destructuring, Spread & Array Practice [`06:51:59`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=24719s) – [`07:12:08`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=25928s)

```js
// Destructuring (skipping index 2) [06:51:59]
let arr = [1, 2, 3, 4, 5];
let [a, b, , c] = arr; // a=1, b=2, c=4

// Cloning with Spread Operator [06:54:04]
let arr2 = [...arr];

// Practice: splice to insert without deleting [06:59:25]
let colors = ["Green", "Yellow"];
colors.splice(1, 0, "Red", "Blue"); // ["Green", "Red", "Blue", "Yellow"]

// Practice: Alphabetical sort & reverse [07:02:05]
let names = ["Zara", "Arjun", "Mira", "Bhavya"];
names.sort().reverse(); // ["Zara", "Mira", "Bhavya", "Arjun"]

// Practice: map squares [07:03:13]
let sq = [1, 2, 3, 4].map(function (val) {
  return val * val;
}); // [1, 4, 9, 16]

// Practice: filter greater than 10 [07:04:04]
let gt10 = [5, 12, 8, 20, 3].filter((val) => val > 10); // [12, 20]

// Practice: every even [07:08:53]
let allEven = [2, 4, 6, 8, 10].every(function (val) {
  return val % 2 === 0;
}); // true

// Practice: Merge & prepend with Spread [07:10:40]
let a1 = [1, 2], b1 = [3, 4];
let merged = [...a1, ...b1]; // [1, 2, 3, 4]

let countries = ["USA", "UK"];
countries = ["India", ...countries]; // ["India", "USA", "UK"]

```

> ⏱ In this snippet: [`06:54:04`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=24844s) · [`06:59:25`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=25165s) · [`07:02:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=25325s) · [`07:03:13`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=25393s) · [`07:04:04`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=25444s) · [`07:08:53`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=25733s) · [`07:10:40`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=25840s)

---

## 8. Objects

### Creation, Dot vs. Bracket Notation, Nesting & Destructuring [`07:23:31`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=26611s) – [`07:32:16`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27136s)

```js
// Creation & Access [07:23:31]
let obj = {
  name: "harsh",
  age: 26,
  khaana: "daal chawal",
};
obj.age;            // 26 (dot notation)
obj["name"];        // "harsh" (bracket notation)

// Dynamic key lookup [07:25:52]
let aa = "name";
obj[aa];            // "harsh" (obj.aa would look for literal key "aa")

// Nested Object, Deep Access & Destructuring [07:29:07]
const user = {
  name: "Harsh",
  address: {
    city: "Bhopal",
    pin: 462001,
    locations: {
      lat: 23.2,
      lng: 77.4,
    },
  },
};
user.address.locations.lng; // 77.4

let { lat, lng } = user.address.locations; // Object destructuring [07:31:16]

```

> ⏱ In this snippet: [`07:25:52`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=26752s) · [`07:29:07`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=26947s) · [`07:31:16`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27076s)

### Looping (`for...in`), `Object.keys`, `Object.entries`, Copying, Optional Chaining & Computed Properties [`07:32:52`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27172s) – [`07:46:35`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27995s)

```js
let obj = {
  name: "harsh",
  age: 26,
  email: "test@test.com",
};

// for...in loop [07:32:52]
for (let key in obj) {
  console.log(key, obj[key]);
}

// Object.keys & Object.entries [07:35:33]
Object.keys(obj);    // ["name", "age", "email"]
Object.entries(obj); // [["name", "harsh"], ["age", 26], ["email", "test@test.com"]]

// Shallow Copy: Spread & Object.assign [07:36:48]
let obj2 = { ...obj };
let obj3 = Object.assign({ price: Infinity }, obj);

// Deep Clone (safe for nested objects) [07:41:23]
let nested = {
  name: "harsh",
  address: { city: "bhopal" },
};
let deepCopy = JSON.parse(JSON.stringify(nested));
deepCopy.address.city = "Indore"; // nested.address.city remains "bhopal"

// Optional Chaining (?.) [07:44:31]
nested?.addresses?.city; // undefined (no error thrown)

// Computed Property Names [07:45:58]
let role = "admin";
let userObj = {
  name: "harsh",
  [role]: "Harsh",  // Creates key "admin": "Harsh"
};

```

> ⏱ In this snippet: [`07:35:33`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27333s) · [`07:36:48`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27408s) · [`07:41:23`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27683s) · [`07:44:31`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27871s) · [`07:45:58`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=27958s)

### Object Practice Questions [`07:47:55`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=28075s) – [`08:00:14`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=28814s)

```js
// Hyphenated key access & destructuring with alias [07:48:02] [07:52:05]
const user = { "first-name": "Harsh" };
user["first-name"]; // "Harsh"
let { "first-name": firstName } = user; // Extracts into variable firstName

// Print key-value pairs using Object.entries [07:54:34]
const course = { title: "JavaScript", duration: "4 weeks" };
Object.entries(course).forEach(function (val) {
  console.log(val[0] + ": " + val[1]);
});

// Safe Optional Chaining on empty object [07:59:05]
const person = {};
console.log(person?.profile?.name); // undefined

// Dynamic Property Assignment [07:59:30]
const key = "role";
let o = {
  name: "harsh",
  [key]: "admin",
};

```

> ⏱ In this snippet: [`07:48:02`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=28082s) · [`07:52:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=28325s) · [`07:54:34`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=28474s) · [`07:59:05`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=28745s) · [`07:59:30`](https://www.youtube.com/watch?v=a-wVHL0lpb0&t=28770s)