# JavaScript Commands Reference

## Variables and Data Types

```javascript
// Variable declaration
var oldVariable = 'old way';  // Function-scoped, hoisted
let variable = 'modern way';  // Block-scoped
const constant = 'cannot reassign';  // Block-scoped, cannot be reassigned

// Data types
let string = 'text';  // String
let number = 42;  // Number
let decimal = 3.14;  // Number (floating point)
let boolean = true;  // Boolean (true/false)
let nullValue = null;  // Null (explicit absence of value)
let undefinedValue;  // Undefined (variable declared but not assigned)
let array = [1, 2, 3];  // Array
let object = { key: 'value' };  // Object
let symbol = Symbol('description');  // Symbol (unique identifier)
let bigInt = 9007199254740991n;  // BigInt (large integers)

// Template literals
let template = `String with ${variable} interpolation`;
let multiline = `Line 1
Line 2`;

// Type checking
typeof variable;  // Returns the type as a string
Array.isArray(array);  // Checks if value is an array
Object.prototype.toString.call(value);  // More precise type checking

// Type conversion
Number('42');  // String to number
String(42);  // Number to string
Boolean(1);  // To boolean
parseInt('42px', 10);  // String to integer with base
parseFloat('3.14');  // String to float
```

## Operators

```javascript
// Arithmetic operators
x + y;  // Addition
x - y;  // Subtraction
x * y;  // Multiplication
x / y;  // Division
x % y;  // Modulus (remainder)
x ** y;  // Exponentiation
++x;  // Increment (prefix)
x++;  // Increment (postfix)
--x;  // Decrement (prefix)
x--;  // Decrement (postfix)

// Assignment operators
x = y;  // Assignment
x += y;  // Addition assignment (x = x + y)
x -= y;  // Subtraction assignment
x *= y;  // Multiplication assignment
x /= y;  // Division assignment
x %= y;  // Modulus assignment
x **= y;  // Exponentiation assignment

// Comparison operators
x == y;  // Equal (with type conversion)
x === y;  // Strict equal (no type conversion)
x != y;  // Not equal (with type conversion)
x !== y;  // Strict not equal (no type conversion)
x > y;  // Greater than
x >= y;  // Greater than or equal
x < y;  // Less than
x <= y;  // Less than or equal

// Logical operators
x && y;  // Logical AND
x || y;  // Logical OR
!x;  // Logical NOT

// Nullish coalescing operator
x ?? y;  // Returns y if x is null or undefined, otherwise x

// Optional chaining
object?.property;  // Returns undefined if object is null/undefined instead of error
array?.[index];  // Safe array access
function?.();  // Safe function call

// Ternary operator
condition ? trueValue : falseValue;

// Spread operator
let newArray = [...array];  // Copy array
let newObject = {...object};  // Copy object
let combined = [...array1, ...array2];  // Combine arrays

// Rest operator
function sum(...numbers) {  // Collect arguments into array
  return numbers.reduce((total, num) => total + num, 0);
}

// Destructuring assignment
let [a, b] = array;  // Array destructuring
let { key1, key2 } = object;  // Object destructuring
let { key1: newName1, key2: newName2 } = object;  // With renaming
```

## Control Flow

```javascript
// Conditional statements
if (condition) {
  // code
} else if (anotherCondition) {
  // code
} else {
  // code
}

// Switch statement
switch (expression) {
  case value1:
    // code
    break;
  case value2:
    // code
    break;
  default:
    // code
}

// Loops
// For loop
for (let i = 0; i < 10; i++) {
  // code
}

// For...in loop (for object properties)
for (let key in object) {
  if (object.hasOwnProperty(key)) {
    // code with object[key]
  }
}

// For...of loop (for iterable values)
for (let value of array) {
  // code with value
}

// While loop
while (condition) {
  // code
}

// Do...while loop
do {
  // code
} while (condition);

// Break and continue
for (let i = 0; i < 10; i++) {
  if (i === 3) continue;  // Skip this iteration
  if (i === 8) break;  // Exit the loop
  // code
}

// Try...catch...finally
try {
  // code that might throw an error
} catch (error) {
  // handle the error
} finally {
  // always executed
}

// Throw custom errors
throw new Error('Something went wrong');
```

## Functions

```javascript
// Function declaration
function functionName(param1, param2) {
  // code
  return result;
}

// Function expression
const functionName = function(param1, param2) {
  // code
  return result;
};

// Arrow function
const functionName = (param1, param2) => {
  // code
  return result;
};

// Arrow function with implicit return
const add = (a, b) => a + b;

// Immediately Invoked Function Expression (IIFE)
(function() {
  // code
})();

(() => {
  // code
})();

// Default parameters
function greet(name = 'Guest') {
  return `Hello, ${name}!`;
}

// Rest parameters
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

// Function with callback
function fetchData(callback) {
  // Async operation
  callback(data);
}

// Higher-order function (returns a function)
function multiplier(factor) {
  return function(number) {
    return number * factor;
  };
}
const double = multiplier(2);
double(5);  // 10

// Method shorthand in objects
const obj = {
  name: 'Object',
  greet() {
    return `Hello, I'm ${this.name}`;
  }
};

// Generator function
function* generator() {
  yield 1;
  yield 2;
  yield 3;
}
const gen = generator();
gen.next();  // { value: 1, done: false }

// Async function
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
  }
}
```

## Objects

```javascript
// Object literal
const person = {
  firstName: 'John',
  lastName: 'Doe',
  age: 30,
  greet() {
    return `Hello, I'm ${this.firstName}`;
  }
};

// Accessing properties
person.firstName;  // Dot notation
person['lastName'];  // Bracket notation

// Setting properties
person.age = 31;
person['job'] = 'Developer';

// Computed property names
const propertyName = 'skill';
const developer = {
  [propertyName]: 'JavaScript'
};

// Object methods
Object.keys(person);  // Array of keys
Object.values(person);  // Array of values
Object.entries(person);  // Array of [key, value] pairs
Object.assign(target, source);  // Copy properties from source to target
Object.freeze(person);  // Make object immutable
Object.seal(person);  // Prevent adding/removing properties
Object.create(prototype);  // Create object with specified prototype

// Property descriptors
Object.defineProperty(person, 'fullName', {
  get() {
    return `${this.firstName} ${this.lastName}`;
  },
  set(value) {
    [this.firstName, this.lastName] = value.split(' ');
  },
  enumerable: true,
  configurable: true
});

// Check if property exists
'firstName' in person;  // true
person.hasOwnProperty('toString');  // false (inherited)

// Object destructuring
const { firstName, lastName, age } = person;
const { firstName: fName, lastName: lName } = person;  // With renaming

// Spread operator with objects
const personWithJob = { ...person, job: 'Developer' };

// Object.fromEntries (array to object)
const entries = [['name', 'John'], ['age', 30]];
const obj = Object.fromEntries(entries);
```

## Arrays

```javascript
// Array creation
const arr1 = [1, 2, 3, 4, 5];
const arr2 = new Array(1, 2, 3, 4, 5);
const arr3 = Array.from('hello');  // ['h', 'e', 'l', 'l', 'o']
const arr4 = Array.of(1, 2, 3);  // [1, 2, 3]

// Accessing elements
arr1[0];  // First element
arr1[arr1.length - 1];  // Last element
arr1.at(0);  // First element
arr1.at(-1);  // Last element

// Modifying arrays
arr1.push(6);  // Add to end
arr1.pop();  // Remove from end
arr1.unshift(0);  // Add to beginning
arr1.shift();  // Remove from beginning
arr1.splice(2, 1, 'a', 'b');  // Remove 1 element at index 2, insert 'a' and 'b'

// Array methods
arr1.concat(arr2);  // Combine arrays
arr1.slice(1, 3);  // Extract portion (not including end index)
arr1.join('-');  // Join elements into string
arr1.reverse();  // Reverse array in place
arr1.sort();  // Sort array in place
arr1.indexOf(3);  // Find index of element
arr1.lastIndexOf(3);  // Find last index of element
arr1.includes(3);  // Check if element exists

// Iterative methods
arr1.forEach((item, index, array) => {
  // Execute for each element
});

arr1.map((item, index, array) => {
  // Return transformed element
  return item * 2;
});

arr1.filter((item, index, array) => {
  // Return true to keep element
  return item > 2;
});

arr1.reduce((accumulator, item, index, array) => {
  // Combine elements into single value
  return accumulator + item;
}, initialValue);

arr1.reduceRight((accumulator, item, index, array) => {
  // Like reduce but right-to-left
  return accumulator + item;
}, initialValue);

arr1.every((item, index, array) => {
  // Return true if all elements pass test
  return item > 0;
});

arr1.some((item, index, array) => {
  // Return true if any element passes test
  return item > 3;
});

arr1.find((item, index, array) => {
  // Return first element that passes test
  return item > 3;
});

arr1.findIndex((item, index, array) => {
  // Return index of first element that passes test
  return item > 3;
});

arr1.findLast((item, index, array) => {
  // Return last element that passes test
  return item > 3;
});

arr1.findLastIndex((item, index, array) => {
  // Return index of last element that passes test
  return item > 3;
});

// Flattening arrays
arr1.flat();  // Flatten one level
arr1.flat(2);  // Flatten two levels
arr1.flat(Infinity);  // Flatten all levels

arr1.flatMap((item, index, array) => {
  // Map and then flatten result by one level
  return [item, item * 2];
});

// Array destructuring
const [first, second, ...rest] = arr1;
const [a, , c] = arr1;  // Skip elements

// Array spread
const combined = [...arr1, ...arr2];
const copy = [...arr1];
```

## Strings

```javascript
// String creation
const str1 = 'Single quotes';
const str2 = "Double quotes";
const str3 = `Template literal with ${variable}`;

// String properties and methods
str1.length;  // String length
str1.charAt(0);  // Character at index
str1.charCodeAt(0);  // UTF-16 code at index
str1[0];  // Character at index (like array)

str1.concat(str2);  // Combine strings
str1.includes('Single');  // Check if contains substring
str1.startsWith('Single');  // Check if starts with substring
str1.endsWith('quotes');  // Check if ends with substring
str1.indexOf('quotes');  // Find position of substring
str1.lastIndexOf('o');  // Find last position of substring

str1.padStart(20, '-');  // Pad start to length
str1.padEnd(20, '-');  // Pad end to length
str1.repeat(3);  // Repeat string

str1.replace('Single', 'Double');  // Replace first occurrence
str1.replaceAll('o', 'O');  // Replace all occurrences

str1.slice(0, 6);  // Extract portion (negative indices from end)
str1.substring(0, 6);  // Extract portion (no negative indices)
str1.substr(0, 6);  // Extract portion (second arg is length)

str1.split(' ');  // Split into array
str1.toLowerCase();  // Convert to lowercase
str1.toUpperCase();  // Convert to uppercase

str1.trim();  // Remove whitespace from both ends
str1.trimStart();  // Remove whitespace from start
str1.trimEnd();  // Remove whitespace from end

// String comparison
str1.localeCompare(str2);  // Compare strings (for sorting)

// Raw string
String.raw`Not \n interpreted`;
```

## Date and Time

```javascript
// Creating dates
const now = new Date();  // Current date and time
const date1 = new Date('2023-01-15T12:30:00');  // From date string
const date2 = new Date(2023, 0, 15, 12, 30, 0);  // Year, month (0-11), day, hour, minute, second
const date3 = new Date(1673789400000);  // From timestamp (milliseconds since epoch)

// Getting date components
now.getFullYear();  // Year (4 digits)
now.getMonth();  // Month (0-11)
now.getDate();  // Day of month (1-31)
now.getDay();  // Day of week (0-6, 0 is Sunday)
now.getHours();  // Hour (0-23)
now.getMinutes();  // Minutes (0-59)
now.getSeconds();  // Seconds (0-59)
now.getMilliseconds();  // Milliseconds (0-999)
now.getTime();  // Timestamp (milliseconds since epoch)

// Setting date components
now.setFullYear(2024);
now.setMonth(11);  // December
now.setDate(31);
now.setHours(23);
now.setMinutes(59);
now.setSeconds(59);
now.setMilliseconds(999);
now.setTime(1704067199999);  // Set by timestamp

// Date formatting
now.toString();  // Full date and time
now.toDateString();  // Date portion
now.toTimeString();  // Time portion
now.toISOString();  // ISO format
now.toUTCString();  // UTC format
now.toLocaleDateString();  // Locale-specific date
now.toLocaleTimeString();  // Locale-specific time
now.toLocaleString();  // Locale-specific date and time

// Date operations
const tomorrow = new Date();
tomorrow.setDate(tomorrow.getDate() + 1);

const diffInMs = date2 - date1;  // Difference in milliseconds
const diffInDays = diffInMs / (1000 * 60 * 60 * 24);  // Convert to days

// Date.now() - current timestamp
const timestamp = Date.now();

// Intl.DateTimeFormat for advanced formatting
const formatter = new Intl.DateTimeFormat('en-US', {
  year: 'numeric',
  month: 'long',
  day: 'numeric',
  hour: 'numeric',
  minute: 'numeric',
  timeZone: 'America/New_York'
});
formatter.format(now);
```

## Regular Expressions

```javascript
// Creating regular expressions
const regex1 = /pattern/;  // Literal notation
const regex2 = /pattern/gi;  // With flags: g (global), i (case-insensitive)
const regex3 = new RegExp('pattern');  // Constructor notation
const regex4 = new RegExp('pattern', 'gi');  // With flags

// RegExp flags
// g - global (find all matches)
// i - ignore case
// m - multiline (^ and $ match start/end of each line)
// s - dotAll (. matches newlines)
// u - unicode
// y - sticky (match from lastIndex only)

// Testing for matches
regex1.test('string');  // Returns true if pattern found

// Finding matches
const match = regex1.exec('string');  // Returns array with match info or null
const matches = 'string'.match(regex1);  // Returns array of matches or null
const matchesAll = 'string'.matchAll(regex1);  // Returns iterator of all matches

// Replacing with regex
'string'.replace(regex1, 'replacement');
'string'.replace(regex1, (match, ...groups) => {
  // Custom replacement function
  return modifiedMatch;
});

// Splitting with regex
'string'.split(regex1);

// Common patterns
const patterns = {
  email: /^[\w.-]+@[\w.-]+\.[a-z]{2,}$/i,
  url: /^(https?:\/\/)?[\w.-]+\.[a-z]{2,}(\S*)$/i,
  phone: /^\+?\d{1,3}[- ]?\d{3}[- ]?\d{4}$/,
  date: /^\d{4}-\d{2}-\d{2}$/,
  ipv4: /^\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}$/,
  password: /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)[a-zA-Z\d]{8,}$/
};

// Capturing groups
const groupRegex = /(\w+)\s(\w+)/;
const result = groupRegex.exec('John Doe');
// result[0] = 'John Doe', result[1] = 'John', result[2] = 'Doe'

// Named capturing groups
const namedGroupRegex = /(?<first>\w+)\s(?<last>\w+)/;
const namedResult = namedGroupRegex.exec('John Doe');
// namedResult.groups.first = 'John', namedResult.groups.last = 'Doe'

// Lookaheads and lookbehinds
const lookaheadRegex = /\w+(?=\s)/;  // Word followed by space
const lookbehindRegex = /(?<=\s)\w+/;  // Word preceded by space
const negativeLookaheadRegex = /\w+(?!\s)/;  // Word not followed by space
const negativeLookbehindRegex = /(?<!\s)\w+/;  // Word not preceded by space
```

## Promises and Async/Await

```javascript
// Creating a promise
const promise = new Promise((resolve, reject) => {
  // Async operation
  if (success) {
    resolve(value);  // Fulfilled with value
  } else {
    reject(error);  // Rejected with error
  }
});

// Consuming promises
promise
  .then(value => {
    // Handle fulfilled promise
    return transformedValue;  // Return for chaining
  })
  .catch(error => {
    // Handle rejected promise
  })
  .finally(() => {
    // Always executed
  });

// Chaining promises
promise
  .then(value1 => {
    return anotherPromise;  // Return another promise
  })
  .then(value2 => {
    // Handle value from anotherPromise
  });

// Promise static methods
Promise.resolve(value);  // Create resolved promise
Promise.reject(error);  // Create rejected promise

Promise.all([promise1, promise2, promise3])  // Wait for all promises
  .then(values => {
    // Array of resolved values
  });

Promise.allSettled([promise1, promise2, promise3])  // Wait for all promises to settle
  .then(results => {
    // Array of objects with status and value/reason
  });

Promise.race([promise1, promise2, promise3])  // First promise to settle
  .then(value => {
    // Value from first resolved promise
  });

Promise.any([promise1, promise2, promise3])  // First promise to fulfill
  .then(value => {
    // Value from first fulfilled promise
  });

// Async/await
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    if (!response.ok) {
      throw new Error(`HTTP error: ${response.status}`);
    }
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
    throw error;  // Re-throw for caller to handle
  }
}

// Using async function
fetchData()
  .then(data => {
    // Use data
  })
  .catch(error => {
    // Handle error
  });

// Async IIFE
(async () => {
  try {
    const data = await fetchData();
    // Use data
  } catch (error) {
    // Handle error
  }
})();

// Parallel async/await
async function fetchMultiple() {
  const [data1, data2] = await Promise.all([
    fetchData('url1'),
    fetchData('url2')
  ]);
  return { data1, data2 };
}
```

## Modules

```javascript
// Exporting (module.js)
export const name = 'Module';
export function greet() {
  return `Hello from ${name}`;
}
export class Person {
  constructor(name) {
    this.name = name;
  }
}
export default function() {
  return 'Default export';
}

// Named exports in a group
export { name, greet, Person };

// Exporting with different names
export { name as moduleName, greet as sayHello };

// Re-exporting from another module
export { function1, function2 } from './other-module.js';
export * from './other-module.js';
export { default } from './other-module.js';

// Importing (app.js)
import defaultExport from './module.js';  // Default import
import { name, greet } from './module.js';  // Named imports
import { name as moduleName } from './module.js';  // Import with alias
import * as module from './module.js';  // Import all as namespace
import defaultExport, { name, greet } from './module.js';  // Default and named

// Dynamic import
import('./module.js')
  .then(module => {
    // Use module
  })
  .catch(error => {
    // Handle error
  });

// With async/await
async function loadModule() {
  try {
    const module = await import('./module.js');
    // Use module
  } catch (error) {
    // Handle error
  }
}
```

## Classes

```javascript
// Class declaration
class Person {
  // Class field
  name = 'Anonymous';
  #privateField = 'Private';  // Private field
  static count = 0;  // Static field
  
  // Constructor
  constructor(name, age) {
    this.name = name;
    this.age = age;
    Person.count++;
  }
  
  // Instance method
  greet() {
    return `Hello, I'm ${this.name}`;
  }
  
  // Getter
  get profile() {
    return `${this.name}, ${this.age} years old`;
  }
  
  // Setter
  set profile(value) {
    [this.name, this.age] = value.split(', ');
    this.age = parseInt(this.age);
  }
  
  // Private method
  #privateMethod() {
    return 'Private';
  }
  
  // Static method
  static create(name, age) {
    return new Person(name, age);
  }
}

// Class inheritance
class Employee extends Person {
  constructor(name, age, job) {
    super(name, age);  // Call parent constructor
    this.job = job;
  }
  
  // Override method
  greet() {
    return `${super.greet()} and I work as a ${this.job}`;
  }
}

// Using classes
const person = new Person('John', 30);
person.greet();
person.profile;  // Getter
person.profile = 'Jane, 25';  // Setter

const employee = new Employee('Jane', 25, 'Developer');
employee.greet();

Person.count;  // Static field
Person.create('Bob', 40);  // Static method
```

## DOM Manipulation

```javascript
// Selecting elements
const element = document.getElementById('id');
const elements = document.getElementsByClassName('class');
const elements = document.getElementsByTagName('div');
const element = document.querySelector('.class');
const elements = document.querySelectorAll('div.class');

// Creating elements
const div = document.createElement('div');
const text = document.createTextNode('Text content');
const fragment = document.createDocumentFragment();

// Modifying elements
element.textContent = 'New text';  // Text content
element.innerHTML = '<span>HTML content</span>';  // HTML content
element.innerText = 'Visible text';  // Visible text

// Attributes
element.getAttribute('attr');
element.setAttribute('attr', 'value');
element.removeAttribute('attr');
element.hasAttribute('attr');

// Classes
element.classList.add('class');
element.classList.remove('class');
element.classList.toggle('class');
element.classList.contains('class');
element.classList.replace('old', 'new');

// Styles
element.style.color = 'red';
element.style.backgroundColor = 'blue';
const styles = getComputedStyle(element);

// DOM structure
element.appendChild(child);
element.insertBefore(newNode, referenceNode);
element.replaceChild(newChild, oldChild);
element.removeChild(child);
element.remove();  // Remove element itself

// Modern insertion methods
element.append(...nodes);  // Add at end (allows multiple nodes and text)
element.prepend(...nodes);  // Add at beginning
element.before(...nodes);  // Add before element
element.after(...nodes);  // Add after element
element.replaceWith(...nodes);  // Replace element

// Navigation
element.parentNode;
element.parentElement;
element.children;  // HTMLCollection of child elements
element.childNodes;  // NodeList of child nodes (elements, text, etc.)
element.firstChild;
element.lastChild;
element.firstElementChild;
element.lastElementChild;
element.nextSibling;
element.previousSibling;
element.nextElementSibling;
element.previousElementSibling;

// Events
element.addEventListener('click', function(event) {
  // Event handler
  event.preventDefault();  // Prevent default action
  event.stopPropagation();  // Stop event bubbling
});

element.removeEventListener('click', handler);

// Common events
// Mouse: click, dblclick, mousedown, mouseup, mousemove, mouseover, mouseout, mouseenter, mouseleave
// Keyboard: keydown, keyup, keypress
// Form: submit, change, input, focus, blur
// Document: DOMContentLoaded, load, resize, scroll
// Drag: dragstart, drag, dragend, dragenter, dragover, dragleave, drop

// Event delegation
document.getElementById('parent').addEventListener('click', function(event) {
  if (event.target.matches('.button')) {
    // Handle button click
  }
});

// Custom events
const customEvent = new CustomEvent('custom', {
  detail: { data: 'value' },
  bubbles: true,
  cancelable: true
});
element.dispatchEvent(customEvent);
```

## Fetch API and AJAX

```javascript
// Basic fetch
fetch('https://api.example.com/data')
  .then(response => {
    if (!response.ok) {
      throw new Error(`HTTP error: ${response.status}`);
    }
    return response.json();  // Parse JSON response
  })
  .then(data => {
    // Use data
  })
  .catch(error => {
    // Handle error
  });

// Fetch with options
fetch('https://api.example.com/data', {
  method: 'POST',  // HTTP method
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer token'
  },
  body: JSON.stringify({ key: 'value' }),  // Request body
  mode: 'cors',  // CORS mode
  credentials: 'include',  // Include cookies
  cache: 'no-cache',  // Cache control
  redirect: 'follow',  // Redirect behavior
  referrerPolicy: 'no-referrer',  // Referrer policy
  signal: abortController.signal  // For aborting request
})
  .then(response => response.json())
  .then(data => {
    // Use data
  });

// Async/await with fetch
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    if (!response.ok) {
      throw new Error(`HTTP error: ${response.status}`);
    }
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
    throw error;
  }
}

// Aborting fetch
const controller = new AbortController();
const signal = controller.signal;

fetch('https://api.example.com/data', { signal })
  .then(response => response.json())
  .then(data => {
    // Use data
  })
  .catch(error => {
    if (error.name === 'AbortError') {
      console.log('Fetch aborted');
    } else {
      console.error('Error:', error);
    }
  });

// Abort after timeout
setTimeout(() => controller.abort(), 5000);  // Abort after 5 seconds

// XMLHttpRequest (older method)
const xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.example.com/data', true);  // Method, URL, async
xhr.setRequestHeader('Content-Type', 'application/json');

xhr.onload = function() {
  if (xhr.status >= 200 && xhr.status < 300) {
    const data = JSON.parse(xhr.responseText);
    // Use data
  } else {
    console.error('Error:', xhr.statusText);
  }
};

xhr.onerror = function() {
  console.error('Network error');
};

xhr.send(JSON.stringify({ key: 'value' }));  // Send with body
```

## Web Storage

```javascript
// Local Storage (persists until explicitly cleared)
localStorage.setItem('key', 'value');  // Store data
const value = localStorage.getItem('key');  // Retrieve data
localStorage.removeItem('key');  // Remove data
localStorage.clear();  // Clear all data
localStorage.key(0);  // Get key by index
localStorage.length;  // Number of items

// Session Storage (persists for session)
sessionStorage.setItem('key', 'value');
const value = sessionStorage.getItem('key');
sessionStorage.removeItem('key');
sessionStorage.clear();
sessionStorage.key(0);
sessionStorage.length;

// Storing objects
localStorage.setItem('user', JSON.stringify({ name: 'John', age: 30 }));
const user = JSON.parse(localStorage.getItem('user'));

// Storage event (for changes from other tabs)
window.addEventListener('storage', event => {
  console.log('Storage changed:', event.key, event.oldValue, event.newValue, event.storageArea);
});

// Cookies
document.cookie = 'name=value; expires=Thu, 01 Jan 2025 00:00:00 UTC; path=/; secure; samesite=strict';

// Reading cookies
const cookies = document.cookie.split('; ').reduce((acc, cookie) => {
  const [name, value] = cookie.split('=');
  acc[name] = decodeURIComponent(value);
  return acc;
}, {});

// IndexedDB (for larger amounts of structured data)
const request = indexedDB.open('database', 1);

request.onupgradeneeded = event => {
  const db = event.target.result;
  const store = db.createObjectStore('users', { keyPath: 'id' });
  store.createIndex('name', 'name', { unique: false });
};

request.onsuccess = event => {
  const db = event.target.result;
  const transaction = db.transaction('users', 'readwrite');
  const store = transaction.objectStore('users');
  
  // Add data
  store.add({ id: 1, name: 'John', age: 30 });
  
  // Get data
  const getRequest = store.get(1);
  getRequest.onsuccess = e => {
    const user = e.target.result;
    console.log(user);
  };
  
  transaction.oncomplete = () => db.close();
};
```

## Error Handling

```javascript
// Try...catch
try {
  // Code that might throw an error
  throw new Error('Something went wrong');
} catch (error) {
  // Handle the error
  console.error('Error:', error.message);
} finally {
  // Always executed
  console.log('Cleanup');
}

// Error types
throw new Error('Generic error');
throw new SyntaxError('Invalid syntax');
throw new TypeError('Invalid type');
throw new ReferenceError('Variable not defined');
throw new RangeError('Value out of range');

// Custom error
class CustomError extends Error {
  constructor(message, code) {
    super(message);
    this.name = 'CustomError';
    this.code = code;
  }
}

throw new CustomError('Custom error message', 'ERR_CUSTOM');

// Async error handling
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    if (!response.ok) {
      throw new Error(`HTTP error: ${response.status}`);
    }
    return await response.json();
  } catch (error) {
    console.error('Error:', error);
    throw error;  // Re-throw for caller to handle
  }
}

// Promise error handling
fetchData()
  .then(data => {
    // Use data
  })
  .catch(error => {
    // Handle error
  });

// Global error handling
window.addEventListener('error', event => {
  console.error('Global error:', event.message, event.filename, event.lineno);
});

window.addEventListener('unhandledrejection', event => {
  console.error('Unhandled promise rejection:', event.reason);
});

// Console methods for debugging
console.log('Info message');
console.error('Error message');
console.warn('Warning message');
console.debug('Debug message');
console.info('Info message');
console.table([{ name: 'John', age: 30 }, { name: 'Jane', age: 25 }]);
console.group('Group');
console.log('Grouped message');
console.groupEnd();
console.time('Timer');
// Code to measure
console.timeEnd('Timer');
console.trace();  // Stack trace
```

## JSON

```javascript
// Converting JavaScript to JSON
const obj = { name: 'John', age: 30, active: true, skills: ['JS', 'HTML'] };
const json = JSON.stringify(obj);  // Convert to JSON string
const prettyJson = JSON.stringify(obj, null, 2);  // Pretty-printed with 2-space indent

// Custom serialization
const customJson = JSON.stringify(obj, (key, value) => {
  if (key === 'age') return undefined;  // Exclude age
  if (typeof value === 'string') return value.toUpperCase();  // Transform strings
  return value;
});

// Converting JSON to JavaScript
const str = '{"name":"John","age":30}';
const parsed = JSON.parse(str);  // Parse JSON string

// Custom deserialization
const customParsed = JSON.parse(str, (key, value) => {
  if (key === 'date') return new Date(value);  // Convert date strings to Date objects
  return value;
});
```

## Timers

```javascript
// setTimeout - run once after delay
const timeoutId = setTimeout(() => {
  console.log('Executed after delay');
}, 1000);  // 1000ms = 1 second

// Clear timeout
clearTimeout(timeoutId);

// setInterval - run repeatedly
const intervalId = setInterval(() => {
  console.log('Executed repeatedly');
}, 1000);  // Every 1 second

// Clear interval
clearInterval(intervalId);

// setTimeout with parameters
setTimeout((a, b) => {
  console.log(a + b);
}, 1000, 5, 10);

// requestAnimationFrame - for animations
function animate() {
  // Update animation
  requestAnimationFrame(animate);
}
const animationId = requestAnimationFrame(animate);

// Cancel animation frame
cancelAnimationFrame(animationId);

// Zero-delay setTimeout
setTimeout(() => {
  // Executed after current script completes
}, 0);

// Using Promise for delay
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

// With async/await
async function delayedFunction() {
  console.log('Start');
  await delay(1000);
  console.log('After 1 second');
}
```

## Miscellaneous

```javascript
// Strict mode
'use strict';

// Debugging
debugger;  // Browser will pause execution if dev tools are open

// Performance measurement
performance.now();  // High-resolution timestamp
performance.mark('start');
// Code to measure
performance.mark('end');
performance.measure('operation', 'start', 'end');
console.log(performance.getEntriesByName('operation'));

// URL manipulation
const url = new URL('https://example.com/path?query=value#hash');
url.hostname;  // 'example.com'
url.pathname;  // '/path'
url.searchParams.get('query');  // 'value'
url.hash;  // '#hash'
url.searchParams.append('new', 'param');
url.toString();  // Full URL with changes

// Clipboard API
async function copyToClipboard(text) {
  try {
    await navigator.clipboard.writeText(text);
    console.log('Copied to clipboard');
  } catch (error) {
    console.error('Failed to copy:', error);
  }
}

async function readFromClipboard() {
  try {
    const text = await navigator.clipboard.readText();
    console.log('From clipboard:', text);
    return text;
  } catch (error) {
    console.error('Failed to read clipboard:', error);
  }
}

// Geolocation API
navigator.geolocation.getCurrentPosition(
  position => {
    const { latitude, longitude } = position.coords;
    console.log(`Location: ${latitude}, ${longitude}`);
  },
  error => {
    console.error('Geolocation error:', error.message);
  },
  {
    enableHighAccuracy: true,
    timeout: 5000,
    maximumAge: 0
  }
);

// Web Workers
const worker = new Worker('worker.js');

worker.postMessage({ command: 'start', data: [1, 2, 3] });

worker.onmessage = event => {
  console.log('Result from worker:', event.data);
};

worker.onerror = error => {
  console.error('Worker error:', error);
};

worker.terminate();  // Stop worker

// Service Workers
navigator.serviceWorker.register('/service-worker.js')
  .then(registration => {
    console.log('Service worker registered:', registration);
  })
  .catch(error => {
    console.error('Service worker registration failed:', error);
  });

// Notifications API
Notification.requestPermission()
  .then(permission => {
    if (permission === 'granted') {
      new Notification('Title', {
        body: 'Notification body',
        icon: 'icon.png'
      });
    }
  });

// Intersection Observer
const observer = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      console.log('Element is visible');
      // Load images, trigger animations, etc.
    }
  });
}, {
  root: null,  // Viewport
  rootMargin: '0px',
  threshold: 0.1  // 10% visible
});

observer.observe(document.querySelector('.element'));
observer.unobserve(element);  // Stop observing
observer.disconnect();  // Stop all observations
```