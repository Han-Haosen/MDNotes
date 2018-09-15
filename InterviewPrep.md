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

