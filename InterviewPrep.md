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