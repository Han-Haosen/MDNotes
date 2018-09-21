#Vue 

vuex, vue-cli, vue-router

you can use small or use big 

## first step

c9.io?

```
new Vue(
    {
        el:'#app;,
        data:{
            msg:'Hello'
            url:'http....'
        }
    }
);

<div id="app">
<h1>{{msg}}</h1>
</div>
```

## data binding:

string interpolation

```
<a href="{{url}}">Home</a>
```

using v-bind or :

v-bind:href="url"

can become :

"url + '?myparam=1'"

v-bind: = :value

Two way databinding:

v-model="email"

e.g

```
<input type="email" v-model="email">
<p>you entered {{email}}</p>
```

v-model.lazy or trim/number 

checkboxes

## Control logic

v-for 

```
<div v-for="interest in interests">
    <input type="checkbox",v-model="selectedInterests" :value="interest">{{interest}}
</div>
```

v-show directive 

```
<p v-show = "selectedInterests.length > 0 >you did</p>
```

v-if directive

v-else //when rendered when v-if fails 

v-else-if

they don't mingle with v-show 

## Event handling 


