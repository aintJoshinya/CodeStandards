# JavaScript Style Guide

## Coding Standards
* All file should follow the general coding standards unless specifically stated here

## Indentation
* The unit of indentation is 2 spaces.
* **Never use tabs**, as this can lead to trouble when opening files in different IDEs/Text editors. Most text editors have a configuration option to change tabs to spaces.

## Quotes
* Use double-quotes `"` for all strings, and use single-quotes `'` for strings within strings.
* This is to stay consistent with other languages that do not use single quotes

```
var greeting = "Hello World!";
var html = "<div class='bold'>Hello World</div>";
```

## Comments
* Follow the General Coding Standards
* It is recommended that classes and public or exported functions should have a comment block `/**...*/` using [JSDoc](http://usejsdoc.org/) style comments.
* Functions should have a comment explaining what the function does and what all of the input parameters are/do.
* Classes should include a block comment containing the description of the class

_JSDocs can be interpreted by IDEs for better intellisense. Below is an example of a JSDoc comment block for a function._

  ```
  /**
   * Takes in a name and returns a greeting string.
   *
   * @param name The name of the greeted person.
   */
  function getGreeting(name) {
      return 'Hello ' + name + '!';
  }
  ```

## Variable Declarations
  * All variables must be declared prior to using them. Use a `var` keyword to define each variable.
  * Global and Implied global variables should never be used.
  * Declare each variable on a newline.

_Proper variable declarations aids in code readability and helps prevent undeclared variables from being hoisted onto the global scope._

  ```
  // Like This
  var a = 2;
  var b = 2;
  var c = 4;

  // Not Like These
  // ------------------------------------------------------
  var a = 2,
      b = 2,
      c = 4;

  // b will be defined on global scope.
  var a = b = 2, c = 4;

  function add(a, b) {
      // c is on the global scope!
      c = 6;

      return a + b + c;
  }
  ```

## Function Declarations
```
// Standard Function Syntax
function foo(param1, param2) {
    return 'foo';
}

// Example of returning a function
function bar(name) {
    var message = "Hello ;

    function greet() {
        return message + name + "!";
    }
    return greet;
}

// Example of returning an object
function foorbar(name) {
    var message = "Hello ";

    var foobar = {
      greet: function(name) {
          return message + name + "!";
        }
    };
    return foobar;
}
```

### Anonymous Functions
* All anonymous functions should be defined as `function() { }`.
* There should be a space between the right parenthesis `)` and the `{`
* The statement body should be indented like a normal function.
* The right curly brace `}` should be on a new line and aligned with the line containing the left curly brace `{` that begins the function statement.

```
element.addEventListener('click', function(ev) { alert('foo'); });

element.addEventListener('click', function(ev) {
    alert('foo');
});
```

## Names
* Follow the General Standard.

### Types
* There are no "types" in JavaScript since it is a scripting language.
* To check type in code, use `typeof`

```
// Example of Checking Type
var x = true;
if(typeof x == "undefined") {}
if(typeof x == "bool") {}
if(typeof x == "number") {}
if(x == null) {}

// Note null != undefined
var x; // undefined
var y = null; // null

function foo(x, y){
  // To check if x or y is defined, do one of the following
  x = x | {} // x = x OR whatever
  if(typeof y != "undefined") {}
}
```

### Classes
* There really aren't class in JavaScript (yet, in the ES6 there will be!)
* Using Object Prototyping class can be accomplished.
* Follow the regular function definitions for this.

## Statements
### Simple
* Each line should contain at most one statement.
* A semicolon should be placed at the end of every simple statement.

### If
_If statements should take the following form:_

```
if (/* condition */) {
    // ...
}

if (/* condition */) {
    // ...
} else {
    // ...
}

if (/* condition */) {
    // ...
} else if (/* condition */) {
    // ...
} else {
    // ...
}
```

### For
_For statements should have the following form:_

```
for(/* initialization */; /* condition */; /* update */) {
    // ...
}
```

### While
_While statements should have the following form:_

```
while (/* condition */) {
    // ...
}
```

### Do While
* Do while statements should be avoided unless absolutely necessary since they are hard to read.
* Do while statements must end with a semicolon `;`

_Do while statements should have to following form:_

```
do {
    // ...
} while (/* condition */);
```

### Switch
* Each switch group except default should end with `break`, `return`, or `throw`.

_Switch statements should have the following form:_

```
// Single Statement in Each Case
switch (/* expression */) {
    case /* expression */: /*Statement*/;  /* termination */;
    case /* expression */: /*Statement*/;  /* termination */;
    case /* expression */: /*Statement*/;  /* termination */;
    default:
        // ...
}

// Multiple Statement in Each Case
switch (/* expression */) {
    case /* expression */:
        // ...
        /* termination */
    case /* expression */:
        // ...
        /* termination */
    default:
        // ...
}
```

### Try
* Try statements should be avoided whenever possible. Use an error parameter in callback functions or reject promises instead.

_Try statements should have the following form:_
```
try {
    // ...
} catch (error) {
    // ...
}

try {
    // ...
} catch (error) {
    // ...
} finally {
    // ...
}
```

### Continue
* It is recommended to take a continue-first approach in all loops.

### Throw
* Avoid the use of the throw statement unless absolutely necessary. See the Try section for details.

## Whitespace
### Black Lines
* Blank lines improve code readability by allowing the developer to logically group code blocks.
* Do not you use then one blank line continuously. Use a comment instead to separate the code

### Blank Space
Blank spaces should be used in the following circumstances.

  * A keyword followed by left parenthesis `(` should be separated by 1 space.
  * All operators except for period `.`, left parenthesis `(`, and left bracket `[` should be separated from their operands by a space.
  * No space should separate a unary/incremental operator `!x, -x, +x, ~x, ++x, --x, x++, x--` and its operand.
  * Each semicolon `;` in the control part of a `for` statement should be followed with a space.

## Object and Array Literals
* Use curly braces `{}` instead of `new Object()`.
* Use brackets `[]` instead of `new Array()`.

## Assignment Expressions
 * Assignment expressions inside of the condition block of `if`, `while`, and `do while` statements should be avoided.

```
// Like This
while (typeof node === 'object') {
    node = node.next;
    // ...
}

// Not Like This
while (node = node.next) {
    // ...
}
```

## === and !== Operators
* There are both `==` && `===` operators in JavaSrcipt / TypeScript. They are slightly different.
* There is much discussion online about the effects of `==` && `!=` vs. `===` & `!==`. It is recommend that one research the difference.
* Equality: `==` and `!=` operators will convert the variables to the same before the comparison (type coercion).
* Identity: `===` and `!==` operators will check for the same type and value.

Example:
```
true == 1; //true, because 'true' is converted to 1 and then compared
"2" == 2;  //true, because "2" is converted to 2 and then compared
true === 1; //false
"2" === 2;  //false
```


## Eval
* **Never use eval**
* **Never use the Function constructor**
* **Never pass strings to `setTimeout` or `setInterval`**

## JSHint / JSCS
* Always use a Linter. The Web Essentials VS Add-In comes with one.
* Use the `.jshintrc` and the `.jscsrc` file in the repository to help keep all code consistent.

Linting your code is very helpful for preventing minor issues that can escape the eye during development.
