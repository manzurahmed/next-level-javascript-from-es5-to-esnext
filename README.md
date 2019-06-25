JavaScript এর এই কোর্সটি Udemy এর একটি ফ্রি কোর্স। এর মেন্টর ছিলেন Md. Al-amin Nowshad। কোর্সটির ভাষা ছিল বাংলা। মডার্ন জাভাস্ক্রিপ্ট শিখবার জন্য এই কোর্সটি একটি সুন্দর প্রারম্ভিক স্টাডি মেটেরিয়াল হতে পারে। যারা ReactJS, VueJS বা AngularJS শুরু করতে চাচ্ছেন, তাদের জন্য জাভাস্ক্রিপ্টের এই মডার্ন ফিচারগুলো জানা থাকা আবশ্যক।

- Udemy Course Link: https://www.udemy.com/course/2287987
- YouTube Playlist: https://www.youtube.com/playlist?list=PLN_rT79fotRRzQl0uQjQbK87pfWj16abq&fbclid=IwAR11yxfwwGgJE7jR37rXzKAt39Fbr07eHpOSyf6rmFgR7EsxZGnz66zzLqk


# 4. Arrow Function

```js
const getCity = str => str.toLowerCase(); // Implicit return
console.log(getCity('Dhaka'));
```

But, if I want to return object, I need to use ({})
```js
	const getCity = str = ({ city: str.toLowerCase() }); // Implicit return
```

*N.B.*: যে সব ক্ষেত্রে ডায়নামিক কনটেক্সট দরকার, this ব্যবহার করতে হবে, সেখানে Arrow function ব্যবহার করা হয় না।

# 5. Default Parameters

```js
function getCity(city = 'Dhaka') {
	return city.toLowerCase();
}

console.log(getCity());
```

# 6. Template Literals

```js
const city = 'Dhaka';
const str = `I live in ${city}`;
console.log(str);
```

# 7. Destructing Assignment

```js
const address = {
	house: {
		no: '32/B/1/3',
		storey: '5th'
	},
	city: 'Dhaka',
	country: 'BD',
	region: 'Asia'
};

// Destructing Assignment on object
const { house, house: { storey }, city } = address;
// Get 'storey' from 'house'
console.log(storey);
console.log(house, city);
// Renaming
const { city: currentCity } = address;
console.log(currentCity);

// Destructuring on Array
const arr =['Dhaka', 1, 2, 3, 4];

function printElements([first = 'default', second]) {
	console.log(first, second);
}

printElements(arr);
```

# 8. Enhanced object literals

```js
const city = 'Dhaka';
const country = 'Bangladesh';

const address = {
	city,
	country
}

console.log(address);
```

# 9. Loop

```js
const arr = [1,2,3,4,5];
arr.forEach(el => console.log(el));
```

forEach এর মধ্যে break; ব্যবহার করা যায় না।

```js
for...of loop
---
for( const el of arr ) {
  if(el === 3) break;

  console.log(el);
}
```

যদি এ্যারে এর ইনডেক্স নিতে চাই,

```js
for( const [i, el] of arr.entries() ) {
  if(el === 3) break;

  console.log(i, el);
}
```

# 10. Promises

সাধারণতঃ ডাটাবেজ থেকে ডাটা নিয়ে আসা ও API কল করার ক্ষেত্রে Promise এর ব্যবহার হয়।

```js
console.log('something 1');
// 5 second span working
console.log('something 2');
```

জাভাস্ক্রিপ্ট লাইন-বাই-লাইন কোড এক্সিকিউট করে থাকে। ধরি, দুইটা console.log এর মাঝে ৫ সেকেন্ডের একটা কাজ করতে হবে। প্রথম console.log এর পরে ৫ সেকেন্ডের কাজের জন্য জাভাস্ক্রিপ্ট বসে না থেকে পরের console.log এক্সিকিউট করে ফেলে। লম্বা কাজটির জন্য ম্যানুয়ালি বসানো না হলে জাভাস্ক্রিপ্ট অনবরত কাজ করতেই থাকবে।
'কাজ ব্লক করে রাখা'র জন্য জাভাস্ক্রিপ্টে Promise ব্যবহার করা হয়।

Promise এ ২টা প্যারামিটার নেয়।

### Basic Example
```js
console.log('something 1');
const p = new Promise(
	(resolve, reject) => {
		setTimeout( () => {
			resolve('RESOLVED!!!');
		}, 5000 );
	}
);
p.then( data => console.log(data) );
console.log('something 2');
```

### More Example
```js
console.log('something 1');
const p = new Promise(
	(resolve, reject) => {
		setTimeout( () => {
			resolve('RESOLVED!!!');
		}, 5000 );
	}
);
p
	.then( data => console.log(data) )
	.catch( err => console.log(err) );
console.log('something 2');
```

### Multiple Promises

Promise.all() এর ক্ষেত্রে সবগুলো প্রমিজ এক্সিকিউট করার পরে সবগুলোরই ডাটা পাওয়া যায়।
```js
console.log('something 1');
const p1 = new Promise(
	(resolve, reject) => {
		setTimeout( () => {
			resolve('from Promise 1');
		}, 5000 );
	}
);
const p2 = new Promise(
	(resolve, reject) => {
		setTimeout( () => {
			resolve('from Promise 2');
		}, 3000 );
	}
);

Promise.all([p1, p2])
	.then( data => console.log(data) )
	.catch( err => console.log(err) )

console.log('something 2');
```

Promise.race() এর ক্ষেত্রে অনেকগুলো প্রমিজ এক্সিকিউট করলে যেটা আগে রিজল্ভ হবে শুধু সেটার ডাটা পাওয়া যাবে। বাকিগুলো পাস হবে না।
```js
Promise.race([p1, p2])
	.then( data => console.log(data) )
	.catch( err => console.log(err) )
```

# 11. Modules

NodeJS বা অন্য কোন ফ্রন্টএন্ড ফ্রেম ব্যবহার করে করা কোন প্রজেক্টে আমরা সাধারণতঃ আমাদের প্রজেক্টকে একাধিক মডিউলে ভাগ করে কাজ করে থাকি। প্রজেক্টের বিভিন্ন অংশ মডিউলে ভাগ করার ফলে প্রজেক্টের বিভিন্ন অংশ রিউইজেবল হয়ে যায়। কাজ করতে সুবিধা হয়।
মডিউল ব্যবহার করার সময় কিছু কিওয়ার্ড নিয়ে কাজ করতে হয়। উদাহরণ হিসাবে বলা যায়, আমার একটা প্রজেক্টে index.js এবং module.js নামে দুইটা ফাইল আছে।

```js
// module.js
const city = 'Dhaka';

const getCity = () => city.toLowerCase();

/*
module.exports = {
	city,
	getCity
};
*/

// Here is modern javascript style
export default {
	city,
	getCity
};
// default ব্যবহার না করে এভাবে export করা যায়
export {
	city,
	getCity
};
...........
// index.js
// এ্যাসাইনমেন্টও destructure করা যায়
//const myModule = require('./module.js');
const { city, getCity } = require('./module.js');
//console.log(myModule.city);
//console.log(myModule.getCity());

// After destructuring
console.log(city, getCity());

// index.js - in Moderm JavaScript style 1
import myModule from './module.js';
console.log(city, getCity());

// index.js - in Moderm JavaScript style 2 - import with destructuring
import {city, getCity} from './module.js';
console.log(ciy, getCity());
```

*Note:* এই অংশটুকু খুব গুরুত্বপূর্ণ। কারণ, ReactJS এ এই কনভেনশন কাজে লাগবে। যেমনঃ
```js
import React, { component } from 'react';
```

# 12. Spread and Rest

Array এবং Object - এই দুইটার ক্ষেত্রেই Spread এবং Rest খুবই গুরুত্বপূর্ণ ফিচার। "..." ৩টা ডট ব্যবহার করে Spread ফিচার করে ব্যবহার করা হয়।

```js
const arr1 = [1,2,3];
const arr2 = [...arr1,4,5];
console.log(arr2);
```

এখানে, ... দিয়ে arr1 এর কন্টেন্টকে arr2 এর মধ্যে নিয়ে আসা (Spread করা) হয়েছে।

Object এর ক্ষেত্রেও Spread ফিচার ব্যবহার করা যায়ঃ যেমনঃ
```js
const obj1 = {
	city: 'Dhaka',
	country: 'Bangladesh'
};

const obj2 = {
	...obj1,
	address: 'East Nayatola' // Adding new property beside using Spread on the previous line
};

console.log(obj2);
```

যদি Spread variable এর কোন প্রোপার্টিকে obj2 তে পরিবর্তন করার প্রয়োজন পরে, তবে, নতুন করে ঐ প্রোপার্টিকে এ্যাসাইন করে দিতে হবে।

```js
const obj2 = {
	...obj1,
	city: 'Rajshahi',
	address: 'East Nayatola' // Adding new property beside using Spread on the previous line
};
```

String কে Spread করলে তা Array তে পরিণত হয়ঃ

```js
const str1 = "A cat is not a tiger."
const arr1 = [...str1];
console.log(arr1);
```

### Rest

Array এর ক্ষেত্রে Rest এর ব্যবহারঃ
```js
const [first, second, ...others] = [1,2,3,4,5,6,7];
console.log(first, second);
console.log(others);

**Output:**
1 2
[3, 4, 5, 6, 7]
```

Array এর ক্ষেত্রে Rest ব্যবহারে Array রিটার্ন করে।

Object এর ক্ষেত্রে Rest এর ব্যবহারঃ
```js
const {c, r, ...others } = {
	c: 'Dhaka',
	r: 'Rajshahi',
	k: 'Khulna',
	j: 'Jessore'
};
console.log(c, r);
console.log(others);

**Output:**
"Dhaka" "Rajshahi"

Object {
  j: "Jessore",
  k: "Khulna"
}
```

Object এর ক্ষেত্রে Rest ব্যবহারে Object রিটার্ন করে।


# 13. SET

Set কে আমরা একটি Object কল্পনা করতে পারি যার শুধু Key আছে, কিন্তু এর বিপরীতে কোন value সেট করা নাই। একটি key একবার যোগ করার পরে ঐ key টি আবার যোগ করা হলে key দ্বিতীয়বার যোগ হবে না; বরং Set এর জন্য key গুলো হবে Unique. এটা সেটের একটা বৈশিষ্ট্য।

```js
const s = new Set();
s.add('new1');
s.add('new2');
s.add('new3');
s.add('new1');
console.log(s);
```

সেট এর মধ্যে কোন key রয়েছে কিনা তা যাচাই করে দেখার জন্য .has ফাংশন ব্যবহার করা হয়।

```js
console.log(s.has('new'));
```

Set এর আরও কিছু ফাংশন রয়েছে, যেমনঃ
- .delete('set1') দিয়ে সেটের key এর নাম দিয়ে যে কোন কি মুছে দেয়া যায়।
- .size দিয়ে সেটে কয়টি key রয়েছে, তা দেখা যায়
- .clear() দিয়ে সেটের সব key একবারে মুছে দেয়া 

Set এর ইলিমেন্টগুলোকে ইটারেট করতে লুপ এর ব্যবহার
```js
for(const k of s) {
	console.log(k);
}
```

Set কে ইনিশিয়ালাইজ করার সময় এর key ডিফাইন করে দেয়া যায়। যেমনঃ 
```js
const s = new Set(['test1', 'test2']);
```

Set কে destructure ও করা যায়। যেমনঃ
```js
const arr = [...s];
console.log(arr);
```

# 14. ARRAY INCLUDES

এ্যারেতে কোন ইলিমেন্ট আছে কিনা চেক করে দেখার জন্য array.includes মেথড ব্যবহার করা হয়।

```js
const arr = [4,5,6,7,8, 'test', 'boom'];
console.log(arr.includes('test'));
```

# 15. EXPONENTIATION OPERATOR

এটি ES6 (2016) এর নতুন একটি ফিচার। আগে ম্যাথ অপারেশনের জন্য Math লাইব্রেরী ব্যবহার করতে হত।

```js
// Before ES6
console.log(Math.pow(2, 4));
console.log(2 ** 4);
```

# 16. ASYNC FUNCTION

যে সমস্ত কাজে একটু বেশী সময় লাগে সে সমস্ত ক্ষেত্রে মডার্ন জাভাস্ক্রিপ্টের আগে কলব্যাক ফাংশন ব্যবহার করা হত। এর পর এলো Promise। মডার্ন জাভাস্ক্রিপ্টে এসেছে async। এই async ফাংশন আন্ডার দ্য হুড promise ব্যবহার করে।

```
const doSomethingAsync = () => {
	return new Promise(resolve => {
		setTimeout(() => resolve('I did something.'), 3000)
	});
}

const client = async () => {
	console.log('Now wait 3 seconds');
	const res = await doSomethingAsync();
	console.log(res);
}
// Call the method
client();
```

# 17. STRING PADDING

কোন স্ট্রিং এর আগে বা পরে কোন নির্দিষ্ট স্ট্রিং দিয়ে প্যাড করার জন্য .padStart এবং padEnd ফাংশন ব্যবহার করা হয়।

```js
"Thank".padStart(8)
"Thank".padEnd(15, '*')
```

# 18. OBJECT METHODS

এই ভিডিওতে object.entries এবং object.values নিয়ে আলোচনা করা হয়েছে।

```js
const obj = {
	a: 'Dhaka',
	b: 'Rajshahi',
	c: 'Khulna'
}

console.log(Object.values(obj));

Output:
Array(3) [
  "Dhaka",
  "Rajshahi",
  "Khulna"
]
```

Object.entries এ অবজেক্টের key এবং value কে Array আকারে রিটার্ন করে থাকে।

```js
const obj = {
	a: 'Dhaka',
	b: 'Rajshahi',
	c: 'Khulna'
}

console.log(Object.entries(obj));

Output:
Array(3) [
  [
    "a",
    "Dhaka"
  ],
  [
    "b",
    "Rajshahi"
  ],
  [
    "c",
    "Khulna"
  ]
]
```

# 19. ARRAY FLAT

Array flat ফাংশন দিয়ে ১ লেভেলের এ্যারেকে সিম্পল এ্যারেতে কনভার্ট করতে এটি ব্যবহার করা হয়।

```js
const arr = [1,2,[3,4],5];
console.log(arr.flat());

Output:
Array(5) [
  1,
  2,
  3,
  4,
  5
]
```

# 20. OPTIONAL CATCH BINDING

জাভাস্ক্রিপ্টে অন্যান্য ল্যাংগুয়েজের মত try...catch ব্লক দিয়ে ইরর হ্যান্ডল করা হয়।

```js
try {
	throw Error();
}
catch (e) {
	console.log(e)
}

তবে ESNext এ catch এ কোন কিছু পাস না করলেও চলবে। যেমনঃ

try {
	throw Error();
}
catch {
	console.error('ERROR');
}
```

# 21. OBJECT fromEntries

Object.entries এর ঠিক উল্টা কাজ এই Object.fromEntries মেথডটি। যদি key, value কম্বিনেশনের এ্যারের এ্যারেরকে অবজেক্টে কনভার্ট করে দিবে।

```js
const arr = [['city', 'Dhaka'], ['country', 'Bangladesh']];
console.log(Object.fromEntries(arr));
```

# 22. STRING TRIM

.trim(), .trimStart() এবং .trimEnd() মাধ্যমে কোন স্ট্রিং এর আগে-পরে, বা, শুরু এবং শেষের স্পেসকে বাদ দিতে পারি।

```js
// const str = "   What the heck is it?      ".trim();
//const str = "   What the heck is it?      ".trimStart();
const str = "   What the heck is it?      ".trimEnd();
console.log(str.length, str);

Output:
20 "What the heck is it?"
26 "What the heck is it?      "
23 "   What the heck is it?"
```

# Array Helper

https://css-tricks.com/an-illustrated-and-musical-guide-to-map-reduce-and-filter-array-methods/

## .map() (Morph Array Piece-by-piece)

```js
const marks = [80, 90, 95, 100, 105];
const doubleMarks = marks.map(mark => mark * 2)
console.log(doubleMarks);

// Output:
[
  160,
  180,
  190,
  200,
  210
]
```

.map() কিভাবে কাজ করেঃ

- .map ফাংশন ইনপুট এ্যারেকে ইটারেট করে প্রত্যেক এলিমেন্টের উপরে কাজ।
- Array রিটার্ন করে।

## .filter()

Array.filter() is a very handy shortcut when we have an array of values and want to filter those values into another array, where each value in the new array is a value that passes a specific test.
 
```
const students = [
  {
    name: "Boops",
    finalGrade: 80
  },
  {
    name: "Kitten",
    finalGrade: 45
  },
  {
    name: "Taco",
    finalGrade: 100
  },
  {
    name: "Lucy",
    finalGrade: 60
  }
]

const passingStudents = students.filter((student) => {
  return student.finalGrade >= 70
})

Output: Array
[
  {
    "name": "Boops",
    "finalGrade": 80
  },
  {
    "name": "Taco",
    "finalGrade": 100
  }
]
```

## .reduce()

The reduce() method takes the input values of an array and returns a single value. This one is really interesting. Reduce accepts a callback function which consists of an accumulator (a value that accumulates each piece of the array, growing like a snowball), the value itself, and the index. It also takes a starting value as a second argument:

```
const fruits = ['mango','lichi','pineapple','blackberry'];

const juicedFruits = fruits.reduce( ( juices, item, index, array ) => {
  return (index < array.length - 1 ? juices += `${item}, ` : juices += `${item}`);
}, '' );
// return (index < array.length - 1) ? sauce += `${cook(item)}, ` : sauce += `${cook(item)}`
console.log(juicedFruits);

Output: String
mango, lichi, pineapple, blackberry
```


## .find()

Return first result satisfying the condition

```
const myNames = [ "m", "a", "n", "z", "u", "r", "a", "h", "m", "e", "d"];
const results = myNames.find( character => character === 'm' ? character : null );
console.log(results);
```
