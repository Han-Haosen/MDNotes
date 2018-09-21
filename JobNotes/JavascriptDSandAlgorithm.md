# Javascript Data structure and Algorithm

template strings

var book = {
  name:'learn'
}

console.log(`you are reading${book.name}.
  new line
  here too`)

```
class Person{
  constructor(name){
    this._name = name;
  }
  get name(){
    return this._name;
  }
}
```

ES2016-- Array.prototype.includes

## Array

var averageTemp = [];
var daysOfWeek = new Array();


averageTemp.push(11.5);

insert in the first position :
```
for(var i = numbers.length; i>=0;i--){
  numbers[i] = numbers[i-1];
}
numbers[0] = -1;
```
or a.unshift(1) does the work

a.pop();

numbers.shift();


numbers.splice(5,3) deleted 3 elements from index 5

concat 连接2个或更多数组，并返回结果

every 对数组中的每一项运行给定函数，如果该函数对每一项都返回true，则返回true

filter 对数组中的每一项运行给定函数，返回该函数会返回true的项组成的数组

forEach 对数组中的每一项运行给定函数。这个方法没有返回值

join 将所有的数组元素连接成一个字符串

indexOf 返回第一个与给定参数相等的数组元素的索引，没有找到则返回-1

lastIndexOf 返回在数组中搜索到的与给定参数相等的元素的索引里最大的值

map 对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组

reverse 颠倒数组中元素的顺序，原先第一个元素现在变成最后一个，同样原先的最后一个元素变成了现
的第一个

slice 传入索引值，将数组里对应索引范围内的元素作为新数组返回
some 对数组中的每一项运行给定函数，如果任一项返回true，则返回true

sort 按照字母顺序对数组排序，支持传入指定排序方法的函数作为参数

toString 将数组作为字符串返回

valueOf 和toString类似，将数组作为字符串返回


## iterate methods

numbers.every(isEven);// isEven is a function that returns true if isEven

it will iterate everything UNTIL false is returned

numbers.some(isEven) -- iterate until return true

numbers.forEach(function(item){
  something
})

or use map and filter

var myMap = numbers.map(isEven);

filter returns a new array that consists of elements that made a function return true

var evenNumbers = numbers.filter(isEven)//all are evenNumbers

Reduce methods


reduce accepts function as parameter

params:previousValue,currentValue,index and Array

function returns a value that adds to adder

return adder after wards

for e.g
```
numbers.reduce(function(previous,current,index{
  return previous+current;
}));



numbers.forEach(x => {
  console.log((x%2==0));
  });

for(let n of numbers){
  console.log(n%2 == 0);
}

```

```
entries方法返回包含键值对的@@iterator，下面是使用这个方法的代码示例：
let aEntries = numbers.entries(); // 得到键值对的迭代器
console.log(aEntries.next().value); // [0, 1] - 位置0的值为1
console.log(aEntries.next().value); // [1, 2] - 位置1的值为2
console.log(aEntries.next().value); // [2, 3] - 位置2的值为3
```


```
let aKeys = numbers.keys(); // 得到数组索引的迭代器
console.log(aKeys.next()); // {value: 0, done: false }
console.log(aKeys.next()); // {value: 1, done: false }
console.log(aKeys.next()); // {value: 2, done: false }
```


```
values方法返回的@@iterator则包含数组的值。使用这个方法的代码示例如下：
let aValues = numbers.values();
console.log(aValues.next()); // {value: 1, done: false }
console.log(aValues.next()); // {value: 2, done: false }
console.log(aValues.next()); // {value: 3, done: false }
```

let numbers2 = Array.from(numbers);

let evens = Array.from(numbers, x => (x % 2 == 0));


numbers.fill() makes all values something

copyArray.copyWithin(0,3) copy from itself

numbers.reverse() to reverse the indexOf

numbers.sort() //automaticlly think it's a strings
```
numbers.sort(function(a,b){
  return a-b;
})
```

```
var friends = [
 {name: 'John', age: 30},
 {name: 'Ana', age: 20},
 {name: 'Chris', age: 25}
];
function comparePerson(a, b){
 if (a.age < b.age){
 return -1
 }
 if (a.age > b.age){
 return 1
 }
 return 0;
}

```


Javascript compares things using ASCII values

## search

indexOf or lastIndexOf

if output -1 means not in

find and findIndex in ES6

take a function and searches for values fit

find returns first value while findIndex returns the index of that vallue

if not fit, find return undefined and findIndex return -1

a.includes(a) // if have true else false

if you pass a starting index, it will start from that position

## type of Array

let myArray = new TypedArray(length)

TypedArray needs to be :

Int8Array 8位二进制补码整数  
Uint8Array 8位无符号整数  
Uint8ClampedArray 8位无符号整数  
Int16Array 16位二进制补码整数  
Uint16Array 16位无符号整数  
Int32Array 32位二进制补码整数  
Uint32Array 32位无符号整数  
Float32Array 32位IEEE浮点数  
Float64Array 64位IEEE浮点数  

## Stack

# Javascript language

javascript objects

mapping strings to values 

# Making your Blog 

4.6 Connecting to your Mongodb 

using Mongolass 
