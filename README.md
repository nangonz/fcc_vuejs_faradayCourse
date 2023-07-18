# Product and Cart Static Code Demo

This is one of the companion repos to the Vue.js course on the freeCodeCamp YouTube channel.
The different demos are each located in their own folder.

**Other Repos from this Tutorial Series**

- [Basic, Static Product Cart Demo](https://github.com/gwenf/vue3-fcc-course-basic-product-cart-demo)
- [Vue CLI Product Cart Demo](https://github.com/gwenf/vue3-fcc-course-vue-cli-product-cart-demo)

Special thanks to [TheJaredWilcurt](https://github.com/TheJaredWilcurt) for helping out with the initial static code and doing pretty much all of the styling.

VueJS is a virtual DOM framework. Virtual DOM make Javascript web applications a littlebit faster and more efficient  
Vue by its self is expremately lightweight (10k gzip). VueJS is called a progressive framework because you can use it  
anywhere from small features on websites where you want to add some interactivity to large scale applications. It is  
extremately flexible. Many companies are using for its incrementaly adaptable nature because if they have a legacy  
application its simple to update their application page by page to turn into a Vue application, into a more modern  
application instead of having to rewrite the whole app at once, that ie one very convenient thing about VueJS.

The Vue project was started in 2013 by its founder Evan You and started to be popular in China where Evan is from. Now  
VueJS has solidify itself as one of the top three Javascript framework. Vue ecosystem includes Vue CLI, Vue Router and  
Vuex. Vue version 3 is compatible with  Vue Router 4 and Vuex 4. In this course we will be using the VueJS core library  
as well as the Vue CLI.  

For more information on Vuex, Vue Router, Vue testing tools and some of the others tools in the Vue ecosystem that are  
not covered in depth in this course you can visit faraday academy in youtube

## Getting Sarted with Vue JS

Since we are gonna be using Vue 3, be sure to visit https://v3.vuejs.org and click "getting started"
You can use Vue directly from a CDN via adding the next script tag in the body tag:

```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<script>
    let app = Vue.createApp({
        data: function() {
            return{
                greeting: 'Hello Vue 3!',
                isVisible: true
            }
        },
        methods: {
            toggleBox () {
                this.isVisible = !this.isVisible
            }
        }
    })
    app.mount('#elementId')
</script>

We are gonna be abble to connect and display data and interact with any kind of DOM element inside of  
Whatever element has the id 'elementId' (usually a div).  
The object inside of 'createApp' is called the option object. Here we are gonna create a data function  
so any variable or function that I'm going to use in my application will live in that object. This function  
needs to return an object with all the variables I want, for example: greeting. To use that variable you just  
have to use {{}} 'double curly braces' (this basicaly means anything found in between will parse as Javascript  
by Vue)

```
Or using CLI (command line interface)
```
> npm init vue@latest
```

## VueJS Directives
They are basically a way to connect elements in our html with the VueJs Javascript. They are like an Html atribute  
but are prepended with a 'v-' to diferenciate them from regular html attributes.  

`v-cloak` it is a convenient utility that will hide anything from rendering until the wholw Vue application is ready.  
Additionaly we have to set a style for this to work.
```css
[v-cloak]{
    display:none;
}
```

`v-model` It is used to establish bidirectional binding between a form element and a component property.
```html
<input v-model="mensaje" type="text">
```

`v-on (o '@')` It is used to associate events to methods or functions in the component. For example: @click.right,  
@click.preven, @keyup.enter, @keydown, among others. What goes after the dot are called event modifiers other example  
is  @click.stop for stop propagation when a click event is triggered. You can also chain them: @click.prevent.stop
```html
<button v-on:click="mostrarMensaje">Haz clic</button>
```

`v-bind (o ':')` It is used to bind dynamic values to HTML attributes.
```html
<a v-bind:href="url">Enlace</a>
```

`v-for` It is used to iterate over a list and render repeated elements.
```html
<ul>
  <li v-for="item in lista" :key="item.id">
    {{ item.nombre }}
  </li>
</ul>
```

`v-if` It is used to condition the rendering of an element based on a Boolean expression.  
`v-show` is similar to v-if but with this attribute the element stills renders in the DOM but with display none. It is  
used in cases where toggle is use frecuently and it will be more perfomant than adding and removing the element from  
the DOM.  
`v-else-if`
`v-else`
```html
<div v-if="mostrarMensaje">
  Este mensaje se muestra si la variable 'mostrarMensaje' es verdadera.
</div>
```


## VueJS Components
To define a Vue Component we gotta do it after our Vue instance and before we mount it to the DOM with app.component.  
This function recieves two arguments, the first one is the name of our custom component, the second one is an options  
object. Since these are self content components any variable you define on data(), you are gonna have to use it inside  
its own template.  

Note that in the example below the template doesn't have syntax highlighting and that's kind of weird, but it is just  
because we are doing it just in one html file. This is just a steping stone to get to more standard ways of creating  
Vue components where you will have syntax highlighting.

```html
<script>
    let app = Vue.createApp({
        data: function() {
            return{
                greeting: 'Hello Vue 3!',
                isVisible: true
            }
        },
        methods: {
            toggleBox () {
                this.isVisible = !this.isVisible
            }
        }
    })
    app.component('loggingForm', {
        template:`
            <form @submit.prevent="handleSubmit">
                <h1>{{title}}</h1>
                <input type="email" v-model="email" />
                <input type="password" v-model="password" />
            </form>
        `,
        data() {
            return {
                title:'Login Form',
                email: '',
                password: ''
            }
        },
        componente: ['custom-input'],
        methods: {
            handleSubmit() {
                console.log(this.email, this.password)
            }
        }
    })
    app.mount('#elementId')
</script>
```

## Compose Components and Components Props  

So what if we want to compose multiple components together. To let the father component know about the child component  
we have to add to the options object a "components" property with an Array of strings (name of the child components we  
want to use in the father component). To pass a property from the father to the child, in the options objet of the  
child we've got to add a "props" property with an Array of strings (names of the properties for example: 'label').

Computed is an object where you can put variables names as keys and whenever this value changes you can get it to run  
getters and setters functions. This is useful to model a variable from a child to a parent because the props we pass to  
childrens are inmutable, we can't change them in the child. there are others ways of handling changing props in the  
child component like passing a function from the parnet to the child, so the child can call functions in the parent and then change variables in that way to. There are also other state management solutions and we will explore all of these  
different options later.

## Loops in Vue
To do this You need to add an Array in data in the options object with all the information you need including the  
the variables that You wanna model. To loop through this Array use "v-for" and dont forget this a for in loop, also  
you need to add a unique key (good practice). You can use loops either for custom components as well as for regular  
elements.

## Components lifecycle hooks
To use lifecycle hooks we have to add a function in the component or vue instance options object.
```javascript
created() {
    console.log('created')
}
mounted() {
    console.log('mounted')
}
unmounted() {
    console.log('unmounted')
}
updated() {
    console.log('updated')
}
```

Why you may want to use a lifecycle hook?, some of the most common use cases are:
1. Check uf user is authorized
2. API Calls (a lot of people use the created and mounted hook to pull data into their application from a backend  
for example)
3. Creating or removing events
4. Geatting or cleaning up data