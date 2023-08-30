<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Give things a good name

```typescript

```

### 👎 Anti-Pattern Example: Use cryptic names you will forget in the future.

```typescript

```

</details>

// TODO remove above this line

# TypeScript Best Practices

This is a guideline of best practices that we can apply to our TypeScript project.
These tips are based on TypeScript documentation, books, articles and professional experience.
Most of these recommendations also apply to JavaScript.

## Table of Contents

[TSBP1. Follow conventions](#tsbp1-follow-conventions)<br/>
[TSBP2. Testing](#tsbp2-testing)<br/>
[TSBP3. Strict configuration](#tsbp3-strict-configuration)<br/>
[TSBP4. Avoid `any`. Type everything](#tsbp4-avoid-any-type-everything)<br/>
[TSBP5. Strings should be safe](#tsbp5-strings-should-be-safe)<br/>
[TSBP6. Call things by their name](#tsbp6-call-things-by-their-name)<br/>
[TSBP7. Use utility types](#tsbp7-use-utility-types)<br/>
[TSBP8. Use const and let](#tsbp8-use-const-and-let)<br/>
[TSBP9. Use === instead of ==](#tsbp9-use--instead-of-)<br/>
[TSBP10. Use shortcut notation sparingly](#tsbp10-use-shortcut-notation-sparingly)<br/>
[TSBP11. Avoid globals](#tsbp11-avoid-globals)<br/>
[TSBP12. Avoid mixing with other technologies](#tsbp12-avoid-mixing-with-other-technologies)<br/>
[TSBP13. Avoid heavy nesting](#tsbp13-avoid-heavy-nesting)<br/>
[TSBP14. Avoid long functions](#tsbp14-avoid-long-functions)<br/>
[TSBP15. Reduce function parameters](#tsbp15-reduce-function-parameters)<br/>
[TSBP16. Do not use flags as function parameters](#tsbp16-do-not-use-flags-as-function-parameters)<br/>
[TSBP17. Comment as much as needed but not more](#tsbp17-comment-as-much-as-needed-but-not-more)<br/>
[TSBP18. Use the ~~fastest~~ most readable way to loop arrays](#tsbp18-no-unnecessary-abstraction)<br/>
[TSBP19. Prefer array methods](#tsbp19-prefer-array-methods)<br/>
[TSBP20. Do not trust any data](#tsbp20-do-not-trust-any-data)<br/>
[TSBP21. Do not use short-hand](#tsbp21-do-not-use-short-hand)<br/>
[TSBP22. Use parameter defaults](#tsbp22-use-parameter-defaults)<br/>
[TSBP23. Use spread and destructuring](#tsbp23-use-spread-and-destructuring)<br/>
[TSBP24. Use template literals](#tsbp24-use-template-literals)<br/>
[TSBP25. End the switches with defaults](#tsbp25-end-the-switches-with-defaults)<br/>
[TSBP26. Use the prefix "is" and "has" for Booleans](#tsbp26-use-the-prefix-is-and-has-for-booleans)<br/>
[TSBP27. Declarations on top](#tsbp27-declarations-on-top)<br/>
[TSBP28. Initialize variables](#tsbp28-initialize-variables)<br/>
[TSBP29. Use iterators and generators](#tsbp29-use-iterators-and-generators)<br/>
[TSBP30. Prefer pure functions](#tsbp30-prefer-pure-functions)<br/>
[TSBP31. Prefer immutability](#tsbp31-prefer-immutability)<br/>
[TSBP32. Avoid side effects](#tsbp32-avoid-side-effects)<br/>
[TSBP33. Avoid magic numbers](#tsbp33-avoid-magic-numbers)<br/>
[TSBP34. Avoid conditionals](#tsbp34-avoid-conditionals)<br/>
[TSBP35. Handle JavaScript errors](#tsbp35-handle-javascript-errors)<br/>
[TSBP36. Prefer promises over callbacks](#tsbp36-prefer-promises-over-callbacks)<br/>
[TSBP37. Do not use weird JavaScript features](#tsbp37-do-not-use-weird-javascript-features)<br/>
[TSBP38. Do not yield to web browser whims](#tsbp38-do-not-yield-to-web-browser-whims)<br/>
[TSBP39. Place scripts at the bottom of the page](#tsbp39-place-scripts-at-the-bottom-of-the-page)<br/>
[TSBP40. Keep DOM access to a minimum](#tsbp40-keep-dom-access-to-a-minimum)<br/>
[TSBP41. Allow configuration and translation](#tsbp41-allow-configuration-and-translation)<br/>
[TSBP42. Progressive Enhancement](#tsbp42-progressive-enhancement)<br/>
[TSBP43. Raw JavaScript is faster](#tsbp43-raw-javascript-is-faster)<br/>
[TSBP44. Organize and remove unused imports](#tsbp44-organize-and-remove-unused-imports)<br/>
[TSBP45. Modularization](#tsbp45-modularization)<br/>
[TSBP46. Lazy-Loading](#tsbp46-lazy-Loading)<br/>
[TSBP47. Compress the files](#tsbp47-compress-the-files)<br/>
[TSBP48. Minify the code](#tsbp48-minify-the-code)<br/>
[TSBP49. Use Google LightHouse](#tsbp49-use-google-lighthouse)<br/>
[TSBP50. Use Web Workers](#tsbp50-use-web-workers)<br/>

## TSBP1: Follow conventions

Code conventions are base rules that allow the creation of a uniform code base across an organization.
Following them does not only increase the uniformity and therefore the quality of the code.
[Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) is very popular and recommended. We can complete them with rules just for TypeScript.
To make it mandatory, we need a linter, formatter and strong code review. The code conventions must be dynamic and adaptable for each team and project.
It is up to each team to define its convention.

## TSBP2: Testing

Testing is more important than shipping.
If we have no tests or an inadequate amount, then every time we ship code, we won't be sure that we didn't break anything.
There's no excuse to not write tests.
There are plenty of good JavaScript test frameworks with typing support for TypeScript.
Always write tests for every new feature/module we introduce.

## TSBP3: Strict configuration

The stricter configuration should be mandatory and should be enabled by default because there is not much value in using Typescript without these few flags.
Otherwise, our types will be too permissive, and it is what we are trying to avoid as much as possible with Typescript.

```json
{
  "forceConsistentCasingInFileNames": true,
  "noImplicitReturns": true,
  "strict": true,
  "noUnusedLocals": true
}
```

The most important one here is the `strict` flag which actually covers four other flags.
We could add independently to progressively introduce Typescript in an existing codebase and slowly get stricter over time: `noImplicitAny`, `noImplicitThis`, `alwaysStrict` and `strictNullChecks`.

## TSBP4: Avoid `any`. Type everything

Always declare variables or constants with a type other than any.
When declaring variables or constants in Typescript without a typing, the typing of the variable/constant will be deduced by the value that gets assigned to it.
This will cause unintended problems.
Another advantage of having good typings in our application is that it makes refactoring easier and safer.
The any type isn't necessarily a bad thing and, in fact, does still come in useful sometimes.
However, in most cases, there is a better alternative that leads to having better defined types overall.
In new projects, it is worth setting `strict:true` in the `tsconfig.json` file to enable all strict type checking options.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use specific types

```typescript
type MyObject = {
  id: number;
  name: string;
};

function getName(value: MyObject): string {
  return value.name;
}
```

### 👎 Anti-Pattern Example: Use `any`

```typescript
function getName(value: any): any {
  return value.name;
}
```

</details>

## TSBP5: Strings should be safe

If we have a variable of type string that can have only a set of values, instead of declaring it as a string type, we can declare the list of possible values as the type.
By declaring the type of the variable appropriately, we can avoid bugs while writing the code during compile time rather than during runtime.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use list of values as type

```typescript
type MyStringType = 'First' | 'Second';

type MyObject = { id: number } & {
  [key in MyStringType]?: string;
};

function getName(value: MyObject, property: MyStringType): string | undefined {
  return value[property];
}
```

### 👎 Anti-Pattern Example: Use `string` as type

```typescript
type MyObject = { id: number } & {
  [key in string]?: string;
};

function getName(value: MyObject, property: string): string | undefined {
  return value[property];
}
```

</details>

## TSBP6: Call things by their name

This is a no-brainer, but it is scary how often you will come across variables like `x1`, `fe2` or `xbqne` in JavaScript, or, on the other end of the spectrum, long variable names like `incrementorForMainLoopFromTenToTwenty` or `createNewMemberIfAgeOverTwentyOneAndMoonIsFull`.
None of these make much sense.
Good variable and function names should be easy to understand and tell us what is going on.
Not more and not less.
One trap to avoid is marrying values and functionality in names.
A function called `isLegalDrinkingAge()` makes more sense than `isOverEighteen()` as the legal drinking age varies from country to country, and there are other things than drinking to consider that are limited by age.
Keeping to English is a good idea, too, because, programming languages are in English.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Give things a good name

```typescript
class User {
  private userId: number;
  private firstName: string;
  private lastName: string;
  private email: string;
  private dateOfBirth: Date;
  private isActive: boolean;

  constructor(
    userId: number,
    firstName: string,
    lastName: string,
    email: string,
    dateOfBirth: Date,
    isActive: boolean,
  ) {
    this.userId = userId;
    this.firstName = firstName;
    this.lastName = lastName;
    this.email = email;
    this.dateOfBirth = dateOfBirth;
    this.isActive = isActive;
  }

  // Getter methods
  getUserId(): number {
    return this.userId;
  }

  getFirstName(): string {
    return this.firstName;
  }

  getLastName(): string {
    return this.lastName;
  }

  getEmail(): string {
    return this.email;
  }

  getDateOfBirth(): Date {
    return this.dateOfBirth;
  }

  isActiveUser(): boolean {
    return this.isActive;
  }
}
```

### 👎 Anti-Pattern Example: Use cryptic names you will forget in the future.

```typescript
class u {
  private id: number;
  private fn: string;
  private ln: string;
  private em: string;
  private dob: Date;
  private a: boolean;

  constructor(i: number, f: string, l: string, e: string, d: Date, a: boolean) {
    this.id = i;
    this.fn = f;
    this.ln = l;
    this.em = e;
    this.dob = d;
    this.a = a;
  }

  gI(): number {
    return this.id;
  }

  getF(): string {
    return this.fn;
  }

  lN(): string {
    return this.ln;
  }

  e(): string {
    return this.em;
  }

  d(): Date {
    return this.dob;
  }

  active(): boolean {
    return this.a;
  }
}
```

</details>

## TSBP7: Use utility types

TypeScript already has a few utility types built-in, such as `Partial<T>`, which makes all properties of `T` optional, or `Readonly<T>`, which makes `T` read-only.
They will help make our code much easier to understand.
As a side note, only try to break interfaces or types into smaller nested interfaces/types if it makes sense from our code's domain point-of-view.
Once they are aggressively split up, it's hard to see the structure, especially when using code completion.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Using utility types.

```typescript
type User = {
  id: number;
  firstName: string;
  lastName: string;
  email: string;
  dateOfBirth: Date;
  isActive: boolean;
};

// Using Partial to create a type for updating user information
type UpdateUser = Partial<User>;

// Using Readonly to create a type for an immutable user
type ImmutableUser = Readonly<User>;

// Using Pick to create a type for a subset of user properties
type UserProfile = Pick<User, 'id' | 'firstName' | 'lastName' | 'email'>;

// Example usage
const user: User = {
  id: 1,
  firstName: 'John',
  lastName: 'Doe',
  email: 'john@example.com',
  dateOfBirth: new Date('1990-01-01'),
  isActive: true,
};

const updatedInfo: UpdateUser = {
  id: 1,
  email: 'updated@example.com',
  isActive: false,
};

// Creating an immutable user
const immutableUser: ImmutableUser = user;

// Creating a user profile with a subset of properties
const userProfile: UserProfile = {
  id: user.id,
  firstName: user.firstName,
  lastName: user.lastName,
  email: user.email,
};

// Attempting to modify properties of an immutable user will result in a type error
// immutableUser.id = 2; // This will cause a compilation error
```

</details>

## TSBP8: Use const and let

JavaScript first searches to see if a variable exists locally, then searches progressively in higher levels of scope until global variables.
`var` is function scope, but, `let` and `const` are block scope. Using `let` and `const` where appropriate makes the intention of the declarations clearer.
It will also help in identifying issues when a value is reassigned to a constant accidentally by throwing a compile time error.
Do use a linter that automates checking and fixing this so that changing let to const doesn't become a delay in code review.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use let

```typescript
function demonstrateVarDangerFixed(): void {
  for (let i = 0; i < 5; i++) {
    setTimeout(function () {
      console.log('Value of i:', i);
    }, 100);
  }
}

demonstrateVarDangerFixed();

// Value of i: 0
// Value of i: 1
// Value of i: 2
// Value of i: 3
// Value of i: 4
```

### 👎 Anti-Pattern Example: Use var

```typescript
function demonstrateVarDanger() {
  for (var i = 0; i < 5; i++) {
    setTimeout(function () {
      console.log('Value of i:', i);
    }, 100);
  }
}

demonstrateVarDanger();

// Value of i: 5
// Value of i: 5
// Value of i: 5
// Value of i: 5
// Value of i: 5
```

</details>

## TSBP9: Use === instead of ==

JavaScript utilizes two different kinds of equality operators: `=== | !==` and `== | !=`.
It is considered best practice to always use the former set when comparing.
If two operands are of the same type and value, then `===` produces `true` and `!==` produces `false`.
However, when working with `==` and `!=`, we'll run into issues when working with different types.
In these cases, they'll try to coerce the values, unsuccessfully.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use `===` and get the right answer.

```typescript
function demonstrateEqualityDangerFixed(): void {
  let numberValue = 5;
  let stringValue = '5';

  if (numberValue === stringValue) {
    console.log('Equal');
  } else {
    console.log('Not Equal');
  }
}

demonstrateEqualityDangerFixed();

// Output: Not Equal
```

### 👎 Anti-Pattern Example: Use `==` and get a false positive

```typescript
function demonstrateEqualityDanger(): void {
  let numberValue = 5;
  let stringValue = '5';

  if (numberValue == stringValue) {
    console.log('Equal');
  } else {
    console.log('Not Equal');
  }
}

demonstrateEqualityDanger();

// Output: Equal
```

</details>

## TSBP10: Use shortcut notation sparingly

Shortcut notation is a tricky subject.
On the one hand it keeps our code small but on the other we might make it hard for other developers.
Well, here's a small list of what can (and should) be done:

- Use `{}` instead of `new Object()`
- Use `''` instead of `new String()`
- Use `0` instead of `new Number()`
- Use `false` instead of `new Boolean()`
- Use `[]` instead of `new Array()`
- Use `/()/` instead of `new RegExp()`
- Use function `(){}` instead of `new Function()`

## TSBP11: Avoid globals

Global variables and function names are an incredibly bad idea.
The reason is that every JavaScript file included in the page runs in the same scope.
If we have global variables or functions in our code, scripts included after ours that contain the same variable and function names will overwrite our variables/functions.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use modules to avoid globals

```html
<!DOCTYPE html>
<!--  index.html -->
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>ES module example</title>
    <script src="a.js" type="module"></script>
    <script src="b.js" type="module"></script>
    <script src="main.js" type="module"></script>
  </head>
  <body></body>
</html>
```

```javascript
// a.js
export function process(a) {
  return `${a} is a string`;
}
```

```javascript
// b.js
export function process(b) {
  return b * 2;
}
```

```javascript
// main.js
import { process as processString } from './a.js';
import { process as processNumber } from './b.js';

console.log(processString('test')); // Output: test is a string
console.log(processNumber(12)); // Output: 24
```

### 👎 Anti-Pattern Example: Function process of `a.js` will be overwritten by process of `b.js` without notice.

```html
<!DOCTYPE html>
<!--  index.html -->
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>ES module example</title>
    <script src="a.js"></script>
    <script src="b.js"></script>
    <script src="main.js"></script>
  </head>
  <body></body>
</html>
```

```javascript
// a.js
function process(a) {
  return `${a} is a string`;
}
```

```javascript
// b.js
function process(b) {
  return b * 2;
}
```

```javascript
// main.js
console.log(process('test')); // Output: NaN
console.log(process(12)); // Output: 24
```

</details>

## TSBP12: Avoid mixing with other technologies

Although it is possible to create everything we need in a document using JavaScript and DOM, it is not necessarily the most effective way of doing so.
Techniques such as [CSS-in-JS](https://en.wikipedia.org/wiki/CSS-in-JS) are very popular.
However, mixing different technologies in the same file, JavaScript, HTML and CSS, it can be dangerous.
A good separation of concerns is always the best practice.

## TSBP13: Avoid heavy nesting

Nesting code explains its logic and makes it much easier to read.
However nesting it too far can also make it hard to follow what we are trying to do.
Readers of our code shouldn't have to scroll horizontally or suffer confusion when their code editors wrap long lines.
The other problem of nesting is variable names and loops.
As we normally start our first loop with as the iterator variable, we'll go on with `j`, `k`, `l` and so on.
This can become messy quite quickly.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use modern methods to keep the code clean.

```typescript
const matrix: number[][][] = [
  [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
  ],
  [
    [10, 11, 12],
    [13, 14, 15],
    [16, 17, 18],
  ],
  [
    [19, 20, 21],
    [22, 23, 24],
    [25, 26, 27],
  ],
];

const flatMatrix = matrix.flat(Infinity);

console.log(flatMatrix); // Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27]
```

### 👎 Anti-Pattern Example: Using nested for-loops will making tracing variables difficult.

```typescript
const matrix: number[][][] = [
  [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9],
  ],
  [
    [10, 11, 12],
    [13, 14, 15],
    [16, 17, 18],
  ],
  [
    [19, 20, 21],
    [22, 23, 24],
    [25, 26, 27],
  ],
];

const flatMatrix: number[] = [];

for (let i = 0; i < matrix.length; i++) {
  for (let j = 0; j < matrix[i].length; j++) {
    for (let k = 0; k < matrix[i][j].length; k++) {
      flatMatrix.push(matrix[i][j][k]);
    }
  }
}

console.log(flatMatrix); // Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27]
```

</details>

## TSBP14: Avoid long functions

Long functions generally indicate that they are doing too many things.
Small functions are better to read and faster to understand the purpose.
If our function has more than 10 lines we need to ask yourself if it would be better to break it into smaller functions.
The best functions or methods are from 5 to 10 lines of code.
The method itself might be doing one thing, but inside it, there are a few other operations that could be happening.
We can extract those methods into their own method and make them do one thing each and use them instead.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: The functionality has been broken down into smaller functions, each responsible for a specific task.

```typescript
function validateOrder(order: Order): boolean {
  // ... code for validating order data
  // ...
  return isValid;
}

function calculateOrderTotal(order: Order): number {
  // ... code for calculating order total
  // ...
  return total;
}

function updateInventory(order: Order): void {
  // ... code for updating inventory
  // ...
}

function generateOrderConfirmation(order: Order): OrderConfirmation {
  // ... code for generating order confirmation
  // ...
  return confirmation;
}

function processOrder(order: Order): void {
  if (validateOrder(order)) {
    const total = calculateOrderTotal(order);
    updateInventory(order);
    const confirmation = generateOrderConfirmation(order);
    // ... any additional code related to processing the order
  } else {
    // ... handle invalid order
  }
}
```

### 👎 Anti-Pattern Example: This can make the function difficult to read, understand, test and maintain.

```typescript
function processOrder(order: Order): void {
  // ... lengthy code for validating order data
  // ... lengthy code for calculating order total
  // ... lengthy code for updating inventory
  // ... lengthy code for generating order confirmation
  // ... more lengthy code...
  // ...
}
```

</details>

## TSBP15: Reduce function parameters

Limiting the amount of function parameters is incredibly important because it makes testing our function easier.
Having more than three leads to a combinatorial explosion of test scenarios.
One or two arguments is the ideal case, and three should be avoided if possible.
Anything more than that should be consolidated.
Usually, if we have more than two arguments then our function is trying to do too much.
In cases where it's not, most of the time a higher-level object will suffice as an argument.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use an Options object

```typescript
type PersonOptions = {
  firstName: string;
  lastName: string;
  age: number;
  gender: string;
  email: string;
};

function createPerson(options: PersonOptions): Person {
  // ... code to create a person object using options
  return person;
}
```

### 👍 Doing It Right Example: Use an Options object with deconstruction.

```typescript
type PersonOptions = {
  firstName: string;
  lastName: string;
  age: number;
  gender: string;
  email: string;
};

function createPerson({
  firstName,
  lastName,
  age,
  gender,
  email,
}: PersonOptions): Person {
  // ... code to create a person object using destructured parameters
  return person;
}
```

### 👎 Anti-Pattern Example: Too many parameters, which will give you problems when some are optional

```typescript
function createPerson(
  firstName: string,
  lastName: string,
  age: number,
  gender: string,
  email: string,
): Person {
  // ... code to create a person object
  return person;
}
```

</details>

## TSBP16: Do not use flags as function parameters

Flags tell our user that this function does more than one thing.
Functions should do one thing.
Split out our functions if they are following different code paths based on a Boolean.
When functions do more than one thing, they are harder to compose, test, and reason about.
When we can isolate a function to just one action, it can be refactored easily, and our code will read much cleaner.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Give things a good name

```typescript
function createOrder({ order, isExpress, sendMail }: OrderOptions): void {
  processOrder(order);

  if (isExpress) {
    processExpressShipping(order);
  }
  if (sendEmail) {
    sendOrderConfirmationEmail(order);
  }
}

function processOrder(order: Order): void {
  // ... lengthy code for processing order
}

function processExpressShipping(order: Order): void {
  // ... code for express shipping
}

function sendOrderConfirmationEmail(order: Order): void {
  // ... code for sending confirmation email
}
```

### 👎 Anti-Pattern Example: Use cryptic names you will forget in the future.

```typescript
function createOrder(
  order: Order,
  isExpress: boolean,
  sendEmail: boolean,
): Order {
  // ... lengthy code for processing order
  if (isExpress) {
    // ... code for express shipping
  }
  if (sendEmail) {
    // ... code for sending confirmation email
  }
}
```

</details>

## TSBP17: Comment as much as needed but not more

Comments are our messages to other developers.
However, if we are adding a comment, it's because it's not self-explanatory and we should choose a better way to implement it.
Good comments are informative comments, when be useful to provide basic information.
Bad Comments are commented-out code is a common practice, but we shouldn't do it, because other developers will think the code is there for a reason and won't have the courage to delete it.
Just delete the code.
Another case is noise comments.
Some comments that we see are just noise.
Redundant comments are comments that are not more informative than the code.
These comments only clutter the code.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Give things a good name without comments

```typescript
/**
 * Calculate the discounted price after applying a discount percentage.
 */
function calculateDiscountPrice(
  price: number,
  discountPercentage: number = 21,
): number {
  const discount = (price * discountPercentage) / 100;

  return price - discount;
}
```

### 👎 Anti-Pattern Example: Too much comments. Like the three times 21% discount.

```typescript
/**
 * Calculate the discounted price after applying a discount percentage.
 * If no discount percentage is provided, a default of 21% is used.
 *
 * @param {number} price - The original price before applying the discount.
 * @param {number} [discountPercentage=21] - The percentage of discount to be applied (default is 21%).
 * @returns {number} The discounted price after applying the discount.
 */
function calculateDiscountPrice(
  price: number,
  percentage: number = 21,
): number {
  // Calculate the discount amount by multiplying price with discount percentage
  // Subtract the discount amount from the original price to get the discounted price
  const p = price - (price * percentage) / 100;

  // Return the discounted price
  return p;
}
```

</details>

## TSBP18: No Unnecessary Abstraction

Don't introduce an extra layer of abstraction. Instead, we directly use map with the conversion function,
keeping the code concise, clear and more reusable.

The `convertToCelsius` function in the example is useful for one item, but also for higher order functions.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: A function that updates one item.

```typescript
function convertToCelsius(fahrenheit: number): number {
  return ((fahrenheit - 32) * 5) / 9;
}

const fahrenheitTemperatures = [32, 68, 104, 212, 451];
const celsiusTemperatures = fahrenheitTemperatures.map(convertToCelsius);

console.log(celsiusTemperatures); // Output: [0, 20, 40, 100, 233]
```

### 👎 Anti-Pattern Example: Too many abstractions.

```typescript
function convertToCelsius(fahrenheit: number): number {
  return ((fahrenheit - 32) * 5) / 9;
}

function convertTemperaturesWithMap(temperatures: number[]): number[] {
  return temperatures.map((temperature) => convertToCelsius(temperature));
}

const fahrenheitTemperatures = [32, 68, 104, 212, 451];
const celsiusTemperatures = convertTemperaturesWithMap(fahrenheitTemperatures);

console.log(celsiusTemperatures); // Output: [0, 20, 40, 100, 233]
```

</details>

## TSBP19: Prefer array methods

There are many ways to loop through array.

- The `for` loop is the fastest way. Caching the `length` makes the loop performs better. Some browser engines have optimized the `for` loop without manually caching the `length` property.
- Using the `forEach` method for arrays, `map`, `filter`, and others.
- There is also the `while` loop.

However, unless we are desperate for performance at the code level (which is rare), make it readable.
In client-side applications, in general, we don't have expensive operations on the client-side. We can use the `for`
loop in server-side applications and the array methods.

It is recommended to use a functional approach without intermediate variables.
The base JavaScript `for` loop can be more performant in some browsers but the benefit can be measured only by iterating over millions of items.
It is job of compiler and runtime to remove penalty of using new array methods.
We should ignore critics and switch to new syntax because it is shorter and more readable.
Another thing, we will use functional programing instead of imperative programing.
The functional programming paradigm was explicitly created to support a pure functional approach to problem-solving.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use the higher order function `filter`.

```typescript
function isEven(number: number): boolean {
  return number % 2 === 0;
}

const numbersArray = [1, 2, 3, 4, 5, 6, 7, 8];
const evenNumbersUsingArrayMethods = numbersArray.filter(isEven);

console.log(evenNumbersUsingArrayMethods); // Output: [2, 4, 6, 8]
```

### 👎 Anti-Pattern Example: A tiny bit, if not measurable, a bit faster, but impossible to follow.

```typescript
function findEvenNumbers(numbers: number[]): number[] {
  const evenNumbers: number[] = [];
  for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] % 2 === 0) {
      evenNumbers.push(numbers[i]);
    }
  }
  return evenNumbers;
}

const numbersArray = [1, 2, 3, 4, 5, 6, 7, 8];
const evenNumbersUsingForLoop = findEvenNumbers(numbersArray);

console.log(evenNumbersUsingForLoop); // Output: [2, 4, 6, 8]
```

</details>

## TSBP20: Do not trust any data

One of the main points to bear in mind when talking about code and data security is not to trust any data.
Make sure that all the data that goes into our systems is clean and exactly what we need.
This is most important on the back-end when writing out parameters retrieved from the URL.
The same applies to forms that validate only on the client side.
Another very insecure practice is to read information from the DOM and use it without validation.

Things to watch out for

- Url query parameters
- Input fields (user input)
- Data from the back-end

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: First sanitize the data before adding to the DOM.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Sanitize example</title>
  </head>
  <body>
    <div id="output"></div>

    <script>
      const queryParams = new URLSearchParams(window.location.search);
      const inputValue = queryParams.get('input');
      const sanitizer = new Sanitizer(); // https://devdocs.io/dom/html_sanitizer_api

      // Escaping and sanitizing user input before writing to the DOM
      const outputDiv = document.getElementById('output');
      outputDiv.setHTML(
        `<p>User input: ${inputValue ?? 'No input provided'}</p>`,
        { sanitizer },
      );
    </script>
  </body>
</html>
```

### 👎 Anti-Pattern Example: Inject user data direct into the DOM

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>No sanitize example</title>
  </head>
  <body>
    <div id="output"></div>

    <script>
      const queryParams = new URLSearchParams(window.location.search);
      const inputValue = queryParams.get('input');

      // Writing query parameter input directly to the DOM (insecure)
      const outputDiv = document.getElementById('output');
      outputDiv.innerHTML = `<p>User input: ${inputValue}</p>`;
    </script>
  </body>
</html>
```

</details>

## TSBP21: Do not use short-hand

Technically, we can get away with omitting most curly braces and semi-colons.

However, this approach is dangerous and not recommended.
This is a terrible practice that should be avoided at all costs.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Be clear

```typescript
function checkNumber(number: number): void {
  if (number > 10) {
    console.log('Number is greater than 10');
  } else {
    console.log('Number is not greater than 10');
  }

  console.log('Yeah!');
}
```

### 👎 Anti-Pattern Example: Use cryptic names you will forget in the future.

```typescript
function checkNumber(number: number): void {
  if (number > 10) console.log('Number is greater than 10');
  else console.log('Number is not greater than 10');
  console.log('Yeah!');
}
```

</details>

## TSBP22: Use parameter defaults

When we call a function and forget to pass a parameter to it, then the missing argument is set to undefined.
ES6 introduced default parameters for the function.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Defaults gives you more clear code.

```typescript
function greet(name: string = 'Guest'): void {
  console.log(`Hello, ${name}!`);
}

greet(); // Output: Hello, Guest!
greet('Alice'); // Output: Hello, Alice!
```

### 👎 Anti-Pattern Example: Writing more code is making more errors.

```typescript
function greet(name?: string): void {
  if (name) {
    console.log(`Hello, ${name}!`);
  } else {
    console.log('Hello, Guest!');
  }
}

greet(); // Output: Hello, Guest!
greet('Alice'); // Output: Hello, Alice!
```

</details>

It is a good habit to assign default values to arguments.

## TSBP23: Use spread and destructuring

The [spread syntax](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_syntax) allows us to expand something that is currently grouped inside a particular container and assign it to a different container.
Compatible containers include: arrays, strings, objects and any iterable (such as Maps, Sets, TypedArrays, etc) and their elements can be expanded into function arguments, array elements and key-value pairs.
Another interesting new feature from JavaScript is [destructuring](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).
This syntax allows us to unpack values from objects and arrays into individual properties.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Using destructuring and spread.

```typescript
type User = {
  name: string;
  age: number;
};

// Good destructuring
function printNameAndAge({ name, age }: User): void {
  console.log(`Name: ${name}, Age: ${age}`);
}

// Good spread usage
const user: User = { name: 'Alice', age: 30 };
const userData = { ...user, role: 'admin' };
console.log(userData); // Output: { name: 'Alice', age: 30, role: 'admin' }

const numbers = [1, 2, 3];
const otherNumbers = [4, 5, 6];
const copiedNumbers = [...numbers, ...otherNumbers, 7];
console.log(copiedNumbers); // Output: [1, 2, 3, 4, 5, 6, 7]
```

### 👎 Anti-Pattern Example: It saves you writing a lot of code and errors.

```typescript
type User = {
  name: string;
  age: number;
};

// Printing name and age without destructuring
function printNameAndAge(person: User) {
  const name = person.name;
  const age = person.age;

  console.log(`Name: ${name}, Age: ${age}`);
}

const user = { name: 'Alice', age: 30 };
const userData = {
  name: user.name,
  age: user.age,
  role: 'admin',
};
console.log(userData); // Output: { name: 'Alice', age: 30, role: 'admin' }

const numbers = [1, 2, 3];
const otherNumbers = [4, 5, 6];
const copiedNumbers = numbers.concat(otherNumbers);
copiedNumbers.push(7);
console.log(copiedNumbers); // Output: [1, 2, 3, 4, 5, 6, 7]
```

</details>

## TSBP24: Use template literals

Template literals make working with strings so much easier than before.
No more long string concatenation.
To create a template literal, instead of single quotes (') or double quotes (") quotes we use the backtick (`) character.
This will produce a new string, and we can use it in any way we want.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Using template literals makes your code clear.

```typescript
const name = 'Alice';
const age = 30;

// Using template literals
const message = `Hello, my name is ${name} and I am ${age} years old.`;

console.log(message); // Output: Hello, my name is Alice and I am 30 years old.
```

```typescript
const fruits = ['apple', 'banana', 'orange'];

// Using template literals for iteration
const list = `
    <ul>
        ${fruits.map((fruit) => `<li>${fruit}</li>`).join('')}
    </ul>
`;

console.log(list); // Output: <ul><li>apple</li><li>banana</li><li>orange</li></ul>
```

### 👎 Anti-Pattern Example: Excessive string concatenation and traditional looping approach

```typescript
const name = 'Alice';
const age = 30;

// Using string concatenation
const message =
  'Hello, my name is ' + name + ' and I am ' + age + ' years old.';

console.log(message); // Output: Hello, my name is Alice and I am 30 years old.
```

```typescript
const fruits = ['apple', 'banana', 'orange'];

// Using string concatenation for iteration
let list = '<ul>';
for (let i = 0; i < fruits.length; i++) {
  list += '<li>' + fruits[i] + '</li>';
}
list += '</ul>';

console.log(list); // Output: <ul><li>apple</li><li>banana</li><li>orange</li></ul>
```

</details>

## TSBP25: End the switches with defaults

Don't leave the switch statements without a default case because something can go wrong, and we want to make sure it is detected.
However, in some cases, it is unnecessary.
To avoid duplicate conditions, we can combine the default statement with another switch statement:

```typescript
function getEmoji(key: string): string {
  switch (key) {
    case 'dog':
      return '🐶';
    case 'cat':
      return '😺';
    // the rest of the emojis...
    case 'smile':
    default:
      return '🙂';
  }
}
```

## TSBP26: Use the prefix "is" and "has" for Booleans

Using variables with prefixes `is` and `has` will communicate clearly that the variable is a Boolean.
The code is read more often than it is written.
Correctly used variable names do not need comments and explanations that can get out of sync with the code rather quickly.
The code is written and should be readable for humans.

## TSBP27: Declarations on top

It is a good coding practice to put all declarations at the top of each script or function.
This will give cleaner code, provide a single place to look for local variables, make it easier to avoid unwanted (implied) global variables and reduce the possibility of unwanted re-declarations.

## TSBP28: Initialize variables

It is a good coding practice to initialize variables when we declare them.
This will give cleaner code, provide a single place to initialize variables and avoid undefined values.
Variables should be declared and initialized at the beginning.

## TSBP29: Use iterators and generators

// TODO Not sure if this is a practical rule.

Use [iterators and generators](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators) when working with collections of data used like a stream.
There are some good reasons such as decouples the call from the generator implementation, lazy execution because the items are streamed on demand, built-in support for iterating items using the `for-of` syntax and iterables allow to implement optimized iterator patterns.

## TSBP30: Prefer pure functions

A [pure function](https://www.freecodecamp.org/news/what-is-a-pure-function-in-javascript-acb887375dfe/) is a function where the return value is only determined by its input values, without observable side effects.
They're easier to reason about, easier to combine, easier to test, easier to debug, easier to parallelize.
Other benefits of writing pure functions for functional programming, for instance, they are idempotent, offer referential transparency, are memoizable and can be lazy.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Give things a good name

```typescript
let externalState = 3;

function pureAdd(a: number, b: number): number {
  return a + b;
}

function pureMultiply(a: number, b: number, multiplier: number): number {
  return a * b * multiplier;
}

function pureRandom(seed: number, min: number, max: number) {
  return seed * (max - min) + min;
}

function pureIO(output: string): string {
  return output; // Return the output instead of performing console.log
}

function pureSideEffect(a: number): { result: number; message: string } {
  const modifiedValue = a + 10;
  return {
    result: modifiedValue * 2,
    message: `Side effect: ${modifiedValue}`,
  };
}

externalState = externalState + pureAdd(3, 4); // Output: 10
console.log(externalState); // Output: 100
console.log(pureMultiply(2, 5, externalState)); // Output: 50
console.log(pureRandom(Math.random(), 1, 10)); // Output: Random number between 1 and 10
console.log(pureIO('Hello, world!')); // Output: "Hello, world!"
console.log(pureSideEffect(5)); // Output: { result: 30, message: "Side effect: 15" }
```

### 👎 Anti-Pattern Example: Use cryptic names you will forget in the future.

```typescript
let externalState = 3;

function impureAdd(a: number, b: number): number {
  // Mistake 1: Modifying external state
  externalState += a + b;
  return externalState;
}

function impureMultiply(a: number, b: number): number {
  // Mistake 2: Reliance on external state
  return a * b * externalState;
}

function impureRandom(min: number, max: number): number {
  // Mistake 3: Non-deterministic output
  return Math.random() * (max - min) + min;
}

function impureIO(output: string): void {
  // Mistake 4: Performing I/O operations
  console.log(output);
}

function impureSideEffect(a: number): number {
  // Mistake 5: Modifying arguments
  a = a + 10;
  console.log(`Side effect: ${a}`);
  return a * 2;
}

console.log(impureAdd(3, 4)); // Output: 10
console.log(impureMultiply(2, 5)); // Output: 100
console.log(impureRandom(1, 10)); // Output: Random number between 1 and 10
console.log(impureIO('Hello, world!')); // Output: "Hello, world!"
console.log(impureSideEffect(5)); // Output: Side effect: 15 & 30
```

</details>

## TSBP31: Prefer immutability

The immutability in JavaScript allows us to differentiate objects and track changes in our objects.
It may sound petty and insignificant, but it turns out to be crucial, especially in front-end applications.
In frameworks such as [Angular](https://angular.io/) and [React](https://reactjs.org/), we'll actually get a performance boost by using immutable data structures.
We gain predictability, change tracking, easiness of implementing reactive interface, change history and others such as testability and a single source of truth.

## TSBP32: Avoid side effects

A function produces a side effect if it does anything other than take a value in and return another value or values.
A side effect could be writing to a file or modifying some global variable.
We do need to have side effects in a program on occasion.
What we want to do is to centralize where we are doing this.
The main point is to avoid common pitfalls like sharing state between objects without any structure, using mutable data types and not centralizing where our side effects occur.

## TSBP33: Avoid magic numbers

Magic numbers are values that appear in source code without any explanation of what they mean.
This makes the code difficult to understand and maintain.
Magic numbers should be avoided as they often lack documentation.
Forcing them to be stored in variables gives them implicit documentation.
With [no-magic-numbers](https://palantir.github.io/tslint/rules/no-magic-numbers/) lint rule, we make code more readable and refactoring easier by ensuring that special numbers are declared as constants to make their meaning explicit.

## TSBP34: Avoid conditionals

This seems like an impossible task.
Upon first hearing this, most people say, "how am I supposed to do anything without an if statement?".
The answer is that we can use polymorphism to achieve the same task in many cases.
The second question is usually, "well that's great but why would I want to do that?".
The answer is the clean code concept, that is, a function should only do one thing.
When we have classes and functions that have if statements, we are telling our user that our function does more than one thing.

## TSBP35: Handle JavaScript errors

Thrown errors are a good thing.
They mean the runtime has successfully identified when something in our program has gone wrong and it's letting us know by stopping function execution on the current stack, killing the process (in Node), and notifying us in the console with a stack trace.
JavaScript as well as TypeScript allow us to throw any object.
A Promise can also be rejected with any reason object.
It is advisable to use the throw syntax with an Error type.
This is because our error might be caught in higher level code with a `catch` syntax.

## TSBP36: Prefer promises over callbacks

Promises are easy to use and anything with a callback can be “promisified”.
Callbacks are synchronous and with promises and `async…await`, we get to do things asynchronous which help speed up the code, especially because JavaScript is single-threaded.

<details><summary>🖊 <b>Code Examples</b></summary>

### 👍 Doing It Right Example: Use a promise function which executes the timeout and log the result on the then()

```typescript
function delayWithPromise(milliseconds: number): Promise<void> {
  return new Promise((resolve) => {
    setTimeout(resolve, milliseconds);
  });
}

delayWithPromise(2000)
  .then(() => {
    console.log('Delayed operation complete');
  })
  .catch((error) => {
    console.error(error);
  });
```

### 👎 Anti-Pattern Example: Do not use a callback function which will be executed after the timeout

```typescript
function delayWithCallback(milliseconds: number, callback: () => void): void {
  setTimeout(() => {
    callback();
  }, milliseconds);
}

delayWithCallback(2000, () => {
  console.log('Delayed operation complete');
});
```

</details>

## TSBP37: Do not use weird JavaScript features

Things like updating array length property, using the `with` keyword, `void` keyword, updating native Object prototypes like Date, Array, Object, etc.
Others like `eval()` function or passing a string to `setTimeout` and `setInterval`.
Just because the language allows us to, does not mean we should.

## TSBP38: Do not yield to web browser whims

Writing code specific to a certain web browser is a sure-fire way to keep our code hard to maintain and make it get dated quickly.
If we look around the web, we'll find a lot of scripts that expect a certain browser and stop working as soon as a new version or another browser comes around.
This is wasted time and effort.
We should build code based on agreed standards.
The web is for everybody, not an elite group of users with a state-of-the-art configuration.
As the browser market moves quickly, we will have to go back to our code and keep fixing it.
This is neither effective.

## TSBP39: Place scripts at the bottom of the page

When loading a script, the browser can't continue until the entire file has been loaded.
Thus, the user will have to wait longer before noticing any progress.
If we have JavaScript files whose only purpose is to add functionality, for example, after a button is clicked, we place those files at the bottom, just before the closing body tag.
The primary goal is to make the page load as quickly as possible for the user.
This is absolutely a best practice.

## TSBP40: Keep DOM access to a minimum

Accessing the DOM in browsers is an expensive thing to do.
The DOM is a very complex API and rendering in browsers can take up a lot of time.
To make sure that our code is fast and doesn't slow down the browser to a halt try to keep DOM access to a bare minimum.
Instead of constantly creating and applying elements, have a tool function that turns a string into DOM elements and call this function at the end of our generation process to disturb the browser rendering once rather than continually.

## TSBP41: Allow configuration and translation

One of the most successful tips to keep our code maintainable and clean is to create a configuration object that contains all the things that are likely to change over time.
If we have this as a part of a module pattern and make it public, we even allow implementers to only override what they need before initializing the module.
It is of utmost importance to keep code maintenance simple, avoiding the need for future maintainers having to read all our code and find where they need to change things.

## TSBP42: Progressive Enhancement

We should do is write code that works regardless of available technology.
In the case of JavaScript, this means that when scripting is not available (say on an old browser, or because of an over-zealous security policy) our web products should still allow users to reach a certain goal, not block them because of the lack of JavaScript which they can't turn on, or don't want to.
For example, imagine links to navigate to other pages after the click action.
The problem starts when the navigation is done by JavaScript.
When JavaScript is disabled, users cannot navigate.
Using the correct HTML construction (Hyperlinks), we were able to get rid of JavaScript.

## TSBP43: Raw JavaScript is faster

JavaScript libraries, such as [jQuery](https://jquery.com/), can save us an enormous amount of time when coding, especially with AJAX operations.
Having said that, always keep in mind that a library can never be as fast as raw JavaScript.
jQuery's `each` method is great for looping, but using a native `for` loop will always be an ounce quicker.

## TSBP44: Organize and remove unused imports

With clean and easy to read import statements we can quickly see the dependencies of current code.
With [no-unused-variable](https://palantir.github.io/tslint/rules/no-unused-variable) lint rule are automatically remove unused imports, variables, functions, and private class members, when using TSLint's --fix option.
[ordered-imports](https://palantir.github.io/tslint/rules/ordered-imports) lint rule requires that import statements be alphabetized and grouped.

## TSBP45: Modularization

This is a general programming best practice.
Making sure that we create functions that fulfill one job at a time makes it easy for other developers to debug and change the code without having to scan through all the code to work out what code block performs what function.
This also applies to creating helper functions for common tasks.
If we are doing the same thing in several different functions then it is a good idea to create a more generic helper function.

## TSBP46: Lazy-Loading

Lazy, or "on demand", loading is a great way to optimize our site or application.
[Lazy loading](https://angular.io/guide/lazy-loading-ngmodules) helps keep initial bundle sizes smaller, which in turn helps decrease load times.
This practice essentially involves splitting our code at logical breakpoints, and then loading it once the user has done something that requires, or will require, a new block of code.
This speed up the initial load of the application and lightens its overall weight as some blocks may never even be loaded.

## TSBP47: Compress the files

Use a compression method such as [Gzip or Brotli](https://medium.com/oyotech/how-brotli-compression-gave-us-37-latency-improvement-14d41e50fee4) to reduce the size of our JavaScript files.
With a smaller sizes file, users will be able to download the asset faster, resulting in improved performance.
In today's web environment, many browsers and servers both support compression.
Its ability to reduce file sizes by up to 70% provides a great incentive to make use of this compression method.
To enable compression is considered a high-priority recommendation by site speed test tools, as without it we are unnecessarily increasing our webpage's load time.

## TSBP48: Minify the code

Bundling our application's components into `*.js` files and passing them through a JavaScript minification program will make our code leaner.
To compress, minimize or minify code simply refers to removing unnecessary characters from the source code like white spaces, new line characters and a host of redundant data without affecting how the code or resource is processed by the browser.
This is a very effective technique otherwise called code minimization that improves the load time of the application and by implication the overall web performance because of a smaller file size.
We can do this by choosing a popular code [minification tool](https://blog.bitsrc.io/10-javascript-compression-tools-and-libraries-for-2019-f141a0b15414).

## TSBP49: Use Google LightHouse

[Google Lighthouse](https://developers.google.com/web/tools/lighthouse) is an open-source, automated tool for improving the quality of web pages.
We can run it against any web page, public or requiring authentication.
It has audits for performance, accessibility, progressive web apps, SEO and more.
We can run Lighthouse in Chrome DevTools, from the command line, or as a Node module.
We can also install it as a plugin in Chrome browser.

## TSBP50: Use Web Workers

Use web workers when we need to execute code that needs a lot of execution time.
Web Workers help us to run scripts in background threads.
The worker thread can perform tasks without interfering with the user interface.
They can perform processor-intensive calculations without blocking the user interface thread.

## Bibliography

- [8 Best Practices for Future-Proofing Your TypeScript Code](https://medium.com/better-programming/8-best-practices-for-future-proofing-your-typescript-code-2600fb7d8063)
- [15 JavaScript Tips: best practices to simplify your code](https://www.educative.io/blog/javascript-tips-simplify-code)
- [19 simple JavaScript coding standards to keep your code clean](https://medium.com/javascript-in-plain-english/19-simple-javascript-coding-standards-to-keep-your-code-clean-7422d6f9bc0)
- [45 Useful JavaScript Tips, Tricks And Best Practices](https://modernweb.com/45-javascript-tips-tricks-practices/)
- [50 Javascript Best Practice Rules to Write Better Code](https://beforesemicolon.medium.com/50-javascript-best-practice-rules-to-write-better-code-86ce731311d7)
- [Clean Code TypeScript](https://github.com/labs42io/clean-code-typescript)
- [Design Patterns](https://refactoring.guru/design-patterns)
- [Design Patterns in TypeScript](https://github.com/torokmark/design_patterns_in_typescript)
- [Five tips I wish I knew when I started with Typescript](https://codeburst.io/five-tips-i-wish-i-knew-when-i-started-with-typescript-c9e8609029db)
- [JavaScript Best Practices for Beginners](https://medium.com/javascript-in-plain-english/javascript-best-practices-for-beginners-b573cbc1ec0f)
- [JavaScript Best Practices](https://www.w3schools.com/js/js_best_practices.asp)
- [JavaScript best practices](https://www.w3.org/wiki/JavaScript_best_practices)
- [TypeScript Style Guide and Coding Conventions](https://github.com/basarat/typescript-book/blob/master/docs/styleguide/styleguide.md)
- [TypeScript: Do's and Don'ts](https://www.typescriptlang.org/docs/handbook/declaration-files/do-s-and-don-ts.html)
- [Typescript Best Practices](https://engineering.zalando.com/posts/2019/02/typescript-best-practices.html)

process een enkele item, geen arrays

No Unnecessary Abstraction:
In this example, we don't introduce an extra layer of abstraction (convertTemperaturesWithMap).'
Instead, we directly use map with the conversion function, keeping the code concise and clear.

geef een functie enkel wat deze nodig heeft.
