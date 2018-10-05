# Javascript 

## Map 

for(),forEach(),map()

Map is not changed
```
var newArr = myArr.map(function(item){
    return item + 1;
})
```

## Reduce

going over and retrieve a single value to do something

```
var total = myArr.reduce(function(inc,item){
    return inc + item;
})
```

arrow function version:

var inc = item => item + 1;
var addEm = (inc,item) => inc + item;

var total = myArr.map(inc).reduce(addEm);

## Animation in CSS

first, definition of the structure of animation 

@keyframes //called an @rule
```
@keyframes myAnime{
    0%{opacity:1;}
    50%{opacity:0.9;}
    100%{opacity:0;}
}
```
```
animation-name, animation-duration, animation-timing-function, animation delay,

etc 

transformation: translate(0) rotate(0deg);
transformation: translate(100vw) rotate(360deg);

```

```
var target = document.querySelector('.mytarget');

target.addEventlistenr('click',function(){
    target.classList.add('myAnimation');
},false)
```


## IIFE

Immediately-invoked function 

function inside IIFE will invoke closures 



## CSS Position 

Absolute and Fixed position 

static, relative, absolute, fixed

Whether it is adjustable 

Static not adjustable 

rest are all adjustable 

absolute and fixed remove them from flow

absolute relative to parent/docuemnt and fixed is relative to document 

.btn:hover .tooltip{
    display:block;
}

## Callback 

do things asynchronously 

often tied to events 

uses anonymous functions 

var tips = document.querySelectorAll('.hastip');

//list type 
```
for(var i=0...){
    tips[i].addEventListener('click',function(e){
    e.target.querySelector('.tooltip').classList.toggle('active');    
    },false);
}
```

## Flexbox 


# Cracking the coding interview

var googol = (number) =>{
    for(let i =0;i<100;i++){
        number = number * number;
    }
    return number;
}

console.log(googol(1));//anything larger than 1 will overflow


Interview prep grid

challenges
mistakes
enjoyed
leadership
conflicts
what will do differently

## BIG O

algorithm is do this then when all done, add run times

do this for each time : multiply 

Amortized time

Arraylist is implmeneted with an array

when array hits capacity, Arraylist class will create a new array with double and copy all into one

-- basically worst case is o(N) but most of the time is O(1)

recursive run time

depth N 

o(2^n)

for a finobacchi recursive call

depth: for a balanced BST, N total nodes depth = log n

all permultations of a string 

```
void permutation(String str){
    permutation(str,"");
}

void permutation(String str, String prefix){
    if length == 0 print(prefix);
}else{
    for(int i=0;i<str.length();i++){
        String rem = str.substring(0,i)+str.substring(i+1);
        permutation(rem,prefix+str.charAt(i))
    }
}
```

through memonization can get O(n)

## Technical questions

Try modularize your cde

Error checks 

use other classes 

good variable names 

need to test it in an interview

double check stuff easily wrong, like base cases, null nodes, integer division 

small test cases 

special cases

BUD -- bottlenecks, unnecessary work, duplicated work 

e.g 

find number of pairs of integers have k diff

use BST since you know the difference already

sort and find other side 

find things quickly? Use hash table 

look for x+k or x-k, look it up in o(N)

e.g ransom note

create hash table that maps from a word to its frequency 

Base case and build 

--for e.g find all permutations to a string

generate by chopping off character and generate all permutations of something less


write flexible and more general purposed code

modular design -- seperate chunk of code

# Array and Strings

## Hashtable:

maps keys to values 

implementations:

1. use an array of linked list and a hash code function


a key might be anything,

compute key's hash value, long or int

map the hash code to an index in array

like hash(key) % array_length


## ArrayList & Resizable Arrays

in some languages, arrays are automatically resizeble 

```
Arraylist<String> merge(String[] words,String[] more){
    ArrayList<String> sentence = newArraylist<>();
    for(string w:words) sentence.add(w);
    for(string w: more)sentence.add(w);
    return sentence;
}
```
StringBuilder


Q1: if string has all unique characters

```
if a string has all unique characters

//idea: use hashtable to see frequency

//first ask if an ASCII or unicode

1. create an array of boolean values,flag and return immediately
2. return false immediately if too long

implemnetation:

boolean isUniqueChars(String str) {
if (str.length() > 128) return false;

 boolean[] char_set = new boolean[128];
 for (int i = 8; i < str.length(); i++){
 int val = str.charAt(i);
 if (char_set[val]) { II Already found this char in string
return false;
}
char_set[val] = true;
}
 return true;
 } 

```
 Q2:if one string is a permutation of the other
```
 //is it case sensitive?
 //if white space is significant
 
 //strings of different length can't be permutation of each other

 solution 1: Sort and compare

 String sort(String s){
     char[] content = s.toCharArray();
     java.util.Arrays.sort(content);
     return new string(content);
 }

 boolean permutation(String s,string t){
     if(s.length() != t.length()){
         return false;
     }
     return sorts(s).equals(sort(t));
 }

solution 2: identical char counts

int[] letters = new int[128];

char[] s_array = s.toCharArray();

for(char c: s_array){
    letters[c]++;
}

for(int i = 0;i < t.length;i++){
    int c = (int)t.charAt(i);
    letters[c]--;
    if < 0{
        return false;
    }
}

return true;
```


Q3: replaces all spaces to "%20"

triple the number of spaces to compute extra chars

implmentation:
```
void replaceSpaces(char[] str, int trueLength) {
int spaceCount = e, index, i = ej
for (i = ej i < trueLengthj i++) {
if (str[i] == ' ') {
    spacecount++;
    }
}
index = trueLength + spaceCount * 2j
if (trueLength < str.length) str[trueLength]
for (i = trueLength - Ij i )= ej i --) {
if (str[i] == ' ') {
str[index - 1] '6';
str[index - 2] = ' 2';
str[index - 3] = '%';
i ndex = index - 3;
} else {
str[index - 1] = str[i];
index--;
}
}
}

```

# Linked list

each point to next node in linked list

doubule linked list

no constant time access to a particular index

delete from linked list
--check for null pointer  
update head or tail pointers  

if require to manage memory, consider if removed should be realloced 

Node deleteNode(Node head,int d){
    Node n = head;
    if(n.data == d){
        return head.next;
    }
    while(n.next != null){
        if(n.next.data == d){
            n.next = n.next.next;
            return head;
        }
        n = n.next;
    }
    return head;
}

may set 2 pointers running at different speed

Q1. Remove duplicate from unsorted linked list

use a simple hash table

iterate through, adding each element, and when discover a duplicate, remove and continue;


# Stacks and Queues 

stack, last in first out 


```
implementing
public class MyStack<T>{
    private static class StackNode<T>{
        private T data;
        private StackNode<T> next;

        public StackNode(T data){
            this.data = data;
        }
    }

    private StackNode<T> top;

    public T pop(){
        if(top == null)throw new EmptyStackException();
        T item = top.data;
        top = top.next;
        return item;
    }

    public void push(T item){
        StackNode<T> t = new StackNode<T>(item);
        t.next = top;
        top = t;
    }

    public T peek(){

    }

    public boolean isEmpty(){
        return top == null;
    }
}
```



# Trees and Graphs

trees are a type of graph

tree is a data structure composed of nodes;

each tree has a root node;

root node has zero or more child nodes;

BST -- every node is all left desc <= n <= all right desc

must be true for BST 

balanced tree or not;

red black trees and AVL trees;

in-order, post-order, pre-order traversal 

```

In order

void inOrderTraversal(TreeNode node){
    if(node != null){
        inOrderTraversal(node.left);
        visit(node);
        inorderTraversal(node.right);
    }
}

Pre Order

void preOrderTraversal(TreeNode node){
    if(node != null){
        visit(node);
        preOrderTraversal(node.left);
        preorderTraversal(node.right);
    }
}

similarly, post order..

left/right then node;

```

## Binary heaps 

Min heap-- complete binary tree(filled except rightmost elemnets on last level)

root is minimum 

insert and extract_min

insert at bottom, insert at right most to maintain complete

fix by swapping new element with its parent until find an appropriate spot , i.e bubble up min element

Extract-Min:

how to remove it?

remove min and swap with last element in the heap, then bubble down



Tries(Prefix Trees)

## Graphs

can be either directed or undirected

consist of multiple isolated subgraphs

can also have cycles

Adjacency List 

every vertext stores a list of adjacent vertices

implementation:

```

class Graph{
    public Node[] nodes;
}

class Node{
    public String name;
    public Node[] children;
}
```

Adjacency Matrices


Graph Search 

depth first search and breadth first search 

DFS -- start at the root and explore each branch completely before moving to next 

BFS -- start at root, explroe each neighbor before going to children

Find shortest path, BFS, if every node, DFS

```
pseudocode implementation of DFS

void search(Node root){
    if(root == null) return;
    visit(root);
    root.visited = true;
    for each (Node n in root.adjacent)[
        if(n.visited == false){
            search(n);
        }
    ]
}

BFS

void search(Node root){
    Queue queue = new Queue();
    root.marked = true;
    queue.enqueue(root);//add to end of queue
    while(!queue.isEmpty()){
        Node r = queue.dequeue()'
        visit(r);
        foreach (Node n in r.adjacent){
            if(n.marked == false){
                n.marked = true;
                queue.enqueue(n);
            }
        }
    }
}
```


Bidirectional search -- 

find the shortest path between a source and destination node

operates by running two simultaneous breadth first searches

when collide, found a path

from O(k^d) to O(k^d/2)



## Bit manipulation 

0110 * 2 = 0110 shifted left by 1

XOR a bit with own negative, always 1

## Quirky Questions

Primality 

## OOP 

Step 1: Handle Ambiguity 

intentionally vague so test whether you make assumpetions or ask clarifying questions

Step 2: Define core objects

Step 3: Analyze relationships 
members?inherit?many to many or one to many?

Step 4: Investigate Actions


Design patterns :

Singleton and Factory

Singleton:

Class only one instance and ensures access to the instance through the application

global object 

```
e.g

private static Restaurant _instance = null;
protected Restaurant(){}
public static Restaurant getInstance(){
    if(_instance == null){
        _instance = new Restaurant()
    }
    return _instance;
}
```

Factory method

interface for creating an instance of a class, with subclasses deciding which to instantiate.

e.g

```
public class Card Game{
    public static CardGame createCardGame(GameType type){
        if(type == GameType.Poker){
            return new PokerGame();
        }else{
            return new BlackJackGame();
        }
    }
}
```


## Recursion and Dynamic Programming 

recursion: built off of subproblems

Bottom-Up approach 

start with simple to two, three and so on

Top-down approach

divide them into subproblems, may overlap

half and half 

Dynamic Programming 

taking recursive and find overlapping subproblems

## Solution to nodes and graphs

No 1 

Given a directed graph, find out whether there is a route

```

BFS

enum State {unvisited,visited,visiting;}

boolean search(Graph g, Node start, Node end){
    if(start = end) return true;

    LinkedList<Node> q = new LinkedList<Node>();
    for(Node u: g.getNodes()){
        u.state = State.unvisited;
    }
    start.state = state.Visiting;
    q.add(start);
    Node u;
    while(!q.isEmpty()){
        u = q.removeFirst();
        if(u != null){
            for(Node v: u.getAdjacent()){
                if(v.state == State.unvisited){
                    if(v == end){
                        return true;
                    }else{
                        v.state = State.Visiting;
                        q.add(v);
                    }
                }
            }
            u.state = State.Visited;
        }
    }
    return false;
}
```


Q2 Given a sorted array with unique integer elements, write an algo to create a BST with minimal height

```
Match number of nodes of L to R

1. insert into T the middle element
2. insert into left the left subarray elements
3. insert the right subarray elements
4. recurse

TreeNode CMBST(int array[]){
    return createMinimalBST(array,0,array.length-1);
}

TreeNode CMBST(int arr[],int start,int end){
    if(end < start){
        return null;
    }
    int mid = (start + end)/2
    TreeNode n = new TreeNode(arr[mid]);
    n.left = CMBST(arr,start,mid-1);
    n.right = CMBST(arr,mid+1,end);
    return n;
}
```

Q3 List of depths 

# GeekforGeeks

Longest Common sequence 

Naive: generate all subsequences and find longest matching

step by step, decrease it like this:

Consider the input strings “ABCDGH” and “AEDFHR. Last characters do not match for the strings. So length of LCS can be written as:

L(“ABCDGH”, “AEDFHR”) = MAX ( L(“ABCDG”, “AEDFHR”), L(“ABCDGH”, “AEDFH”) )

expontential not good

use memonization or tabulation to do it 



# JS interview questions 

No 1 Let vs Const

let is block scoped 

const don't let you change value

const c; //c = undefined can't change 

var hoisting 

object const can't reassign but can modify 

difference between null and undefined?

empty value

when declare but not define it yet,undefined

null is you do it yourself 

typeof(null) = object 

arrow function 

arrow function 

the this.firstName might be linked to window object 

prototypal inheritance 

objects have a property called prototype 

e.g
```
let car = function(model){
    this.model = model;
}

car.protytype.getModel = function(){
    return this.model;
}

let toyota = new car('a');
console.log(toyota.getModel());

```

promises 

let a = function(){

}

didn't get hoisted 

$.ajax({
    url:"a.json"
    success:function(r){
        $.ajax({
            url:"b.json" + r.a,
            success...
        })
    }
})

traditional way 

var p1 = new Promise(function(resolve,reject){
    resolve($.ajax('a.json');)
});

p1.then(function(r)){
    return new Promise()
}).then(function(result){
    ...
})


setTimeout()

console.log('a');

setTimeout(function(){
    console.log('a');
},0);

actually b c and a even though 0 time out

async comes after sync 

closure 

let obj = function(){
    let i = 0;

    return {
        setI(k){
            i=k;
        },
        getI(){
            return i;
        }
    }
}

let x = obj();

x.setI(2);
console.log(x.getI());
returns 2 but you can't access it 


## Mock interviews 

something you have done in JS?

let x = {
    a:1,
    b:2
};

xArr = [];
for(i in x){
    xArr.push(i);
}//?

str.split('').reverse().join('');

Object.values

const obj = {
    a:1,
    a:2,
    getA(){
        console.log(this.a)
        return this;
    },
    getB(){
        console.log(this.b)
    }
}

obj.getA().getB();

[1,2].print();

Array.prototype.print = () =>{
    //dynamic method
    /*
    let result = '';
    this.forEach(elem => {
        result += `${elem},`;//add an if to avoid extra comma
    })
    console.log(result);


    */
    console.log(`${this[0],$this[1]}`);//specific cases
}

const a = function(x){
    this.x = x;
};
a.prototype = {
    getX()[
        return this.x;
    ]
}

const b = function(x,y){
    this.y = y;
    a.call(this.x)
};

const newB = new b('x','y');

object.defineProperty(object, descriptors)

object.defineProperty(person,"language",{value:"yes"}),


object.entries(obj) //return pairs
object.keys(obj);
Object.values(obj);

function Person()[

]
Person.prototype.nationality = "English"

JS Forms 

function validateForm(){
    var x = document.forms["myForm"]["fname"].value;
    if (x == ""){
        ...
    }
}
```
<form name="myForm" action="/action_page.php" onsubmit="return validateForm()" method="post">
Name: <input type="text" name="fname">
<input type="submit" value="Submit">
</form>
```

required attribute 

Array.find(func) returns value that passes a test 

Array.findIndex()

index of the first array element that passes a function 

isInteger 

isSafeInteger 

Arrow function have NO this 

functions are hoisted, not functions defined using an expression 

function expressions will execute auto if followed by ()

```
(function () {
    var x = "Hello!!";      // I will invoke myself
})();
```

accessing using arguments object 

```
x = findMax(1, 123, 500, 115, 44, 88);

function findMax() {
    var i;
    var max = -Infinity;
    for (i = 0; i < arguments.length; i++) {
        if (arguments[i] > max) {
            max = arguments[i];
        }
    }
    return max;
}
```


# JS DOM operations 


all HTML elements are defined as objects 


document.getElementByID("demo").innerHTML = "a";

finding HTML elements:

document.getElementsByTagName()
document.getElementsByClassName()

element.innterHTML
element.attribute
element.setAttribute(attribute,value)
element.style.property = new style 

document.createElement()
document.removeChild()
document.appendChild()
document.replaceChild(element)

document.getElementById(id).onclick = function(){code}

var x = document.querySelectorAll("p.intro");

document.write(Date());//don;t do it real 

document.getElementbyId("image").src = ...

html style 

style.visibility = 'hidden' or 'visible'

## Animation

gradual changes in an element

var id = setInterval(frame,5);

function frame(){
    if(finished){
        clearInterval(id);
    }else{

    }
}

## Events 

onload/onunload

onchange

onmouseover/onmouseout

onmousedown, onmouseup and onclick Events

addEventListener 

document.getElementByID("myBtn").addEventListener("click",displayDate);

addEventListener() method attaches an event handler to an element without overwriting existing event handlers.

removeEventListener()

element.addEventlistener(event,function,useCapture)

whether use event bubblign or event capturing (optional)

Event propagation is a way of defining the element order when an event occurs. If you have a <p> element inside a <div> element, and the user clicks on the <p> element, which element's "click" event should be handled first?

to handle first or last for nested elements

bubbling -- inner first 

capturing out handled first 

default is false i.e bubbling propagation 

parentNode
childNodes[nodenumber]
firstChild
lastChild
nextSibling
previousSibling

function loadDoc(){
    var xhttp = new XMLHttpRequest();
    xhttp.onreadystatechange = function(){
        if(this.readyState === 4 && this.status === 200){
            doicument.getElementById().innerHTML = this.responseText;
        }
    };
    xhttp.open("GET","ajax_info.txt",true);
    xhttp.send();
}

xhttp.abort()
xhttp.getAllResponseHeaders()
xhttp.open(method, url, async, user, psw)

async true = async or false 

sent() for get
send(string) for post

setRequestHeader()

localStorage.getItem()/setItem()

obj = JSON.parse(text);

JSON.stringify(obj);

person["name"]

person.name;


JSON + AJAX

```
var xmlhttp = new XMLHttpRequest();
xmlhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
        var myObj = JSON.parse(this.responseText);
        document.getElementById("demo").innerHTML = myObj.name;
    }
};
xmlhttp.open("GET", "json_demo.txt", true);
xmlhttp.send();
```

obj.date = new Date(obj.raw);

## Node JS 

event emitter 

var myEventHandler = function(){

}

var eventEmitter = new events.EventEmitter();

eventEmitter.on('event',myEventHandler);

eventEmitter.emit('scream');

MongoDB

```
var MongoClient = require('mongodb').MongoClient;
var url = "mongodb://localhost:27017/";

MongoClient.connect(url, function(err, db) {
  if (err) throw err;
  var dbo = db.db("mydb");
  var myobj = { name: "Company Inc", address: "Highway 37" };
  dbo.collection("customers").insertOne(myobj, function(err, res) {
    if (err) throw err;
    console.log("1 document inserted");
    db.close();
  });
});
```

find is findOne()

find(query)

when sort, 1 is ascending -1 is descending 

Fetch API

full access to features 

fetch(url).then(function(response){
    return response.json();
}).then(function(data){
    console.log(data);
});

