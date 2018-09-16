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

