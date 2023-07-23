# Product and Cart Vue CLI Demo

This is one of the companion repos to the Vue.js course on the freeCodeCamp YouTube channel.
You can see the different stages of development by checking out the other branches.

**Other Repos from this Tutorial Series**

- [Static files from initial lessons](https://github.com/gwenf/vue3-fcc-course-static-code)
- [Basic, Static Product Cart Demo](https://github.com/gwenf/vue3-fcc-course-basic-product-cart-demo)

Special thanks to [TheJaredWilcurt](https://github.com/TheJaredWilcurt) for helping out with the initial static code and doing pretty much all of the styling.

## Getting started with Vue CLI  (Command Line Interface)
https://cli.vuejs.org/guide/installation.html
Install vue cli package globally so that from your command line or terminal, you're gonna be able to use Vue command to  
create projects. Now you might see some places on the internet that install a different package without the at (@)  
sign. That is an older version of the package Vue basically has its own namespace and then each one of its packages are after the forward slash. Once you have the Vue CLI installed, you can check and make sure that it's installed by  
checking the version.

Right now I have version 4.5 point 11.
```
npm install -g  @vue/cli
vue --version
```

Now you can create a new Vue porject with the command:
```
vue create projectName
```
Now, if you've used some tools like create react app, you will notice that here, it's a little bit different.  
It doesn't just bootstrap the whole project for you right away, you actually get to pick your own options, and the packages that you want to install and use. Now you'll notice a multi select. And if I press spacebar, I can select or deselect an item.
- Babel
- Typescript
- Progressive Web App support
- Router
- Vuex
- CSS Pre-processors
- Linter/Formatter
- Unit Testing
- E2E Testing

In this project we are using babel for transpiling our Vue code, Router, also Vuex (state management). If you think you  
will want to use a pre-processor like sass or less you can select it too. You definitely want linter and formatter in  
this project (ESLint + Standard configs). Additionally you can choose placing your config for babel, ESLint, etc in  
dedicated config files or in one package.json. Usually when you have larger projects, you want dedicated config files  
so it's not cluttering up your package dot JSON. It also initialize a git repository for you, and saved all of the changes that it did initially as a commit. And you have your complete project created by Vue.

### Vue Folder structure
Starting with the Vue, CLI gives us a lot more features out of the box that we can see in the package dot JSON,  
we have three scripts here by default. It gives us our main two commands for the Vue application for development  locally, it gives us a serve command, which basically calls the package vcli service. The build command is really for   when we want to host our project live. This will generate production ready files for you like your HTML, CSS, and JavaScript. So you can deploy them and have a live website somewhere.

1. **Public**
	- *index.html*: inside we have a dib with the ID app. This is where our app will be injected. But also when our  
	application is built. Under the hood, this vue CLI service command is running webpack and bundling all of aour files  
	together and also handling running Babel to transpile our files, and so all of the javascript and everything will be  
	injected as a script tag as well there. But we generally don't have to worry about this index.html in a Vue project  
	because again most of what we will be doing is in the source folder.
2. **Source**
	- `main.js`:  


		```javascript
		import { createApp } from 'Vue'
		ímport App from './App.vue'
		import router from './router'

		createApp(App).use(router).mount('#app')

		//o también
		const app = createApp(App)
		app.use(router)
		app.mount('#app')
		```


		Just like before we have to pass in a root component, we chain any package we want to use, in this case, the router  
		and then we mount that to the DOM so inside of the div with id of 'app'

	- `App.vue`: this is our main component. You will notice there is a `<router-link>` and a `<router-view>` tag.  
		`<router-link>` is a custom component, this come from the app.use(router) and is a substitution for the `<a>` tag  
		specifically for single page application routing where our javascript hadles the routing instead of linking to a  
		separate HTML page. Of course we only have one HTML page, and all of our static content is injected into that one.  
		The router handles intercepting the route and making it appear a though you've navigated to another page while  
		really it's just showing and hiding elements on the DOM. `<router-view>` is our page content and our router will  
		handle replacing this router Vue tag with whatever component we tell it to in our routes file. So router-view is  
		just a temporary placeholder for whatever we put on the page.

	- `assets`: assets, of course, are a place for usually CSS images, anything like that to live.
	- `components`: in front end applications, files are usually split up between Vues, or pages. So basically, anything  
		in viewa folder will be connected to the router. So they will have their own routes, there'll be their own pages.  
		Anything in the components folder are things that are imported into other components. They're meant to be parts of  
		pages or reusable components that you use throughout your application. Basically, anything in the Vues folder is  
		connected to the router.
	- `router` 
	- `views`

Sometimes you will see other folders created here in Vue projects but these are the basic ones. The only one that we  
are going to add later is the store folder.

### Vue Router
Because we chose to install a router as well, it installed the default Vue router, which is also called Vue router.  
And you can see I can go to different page routes. Now this isn't the same as our last application, because there's  
no page refresh in between page routes. These are not HTML links. This is just a JavaScript router, rendering hiding or showing different pages of this application.

Now, you don't have to worry about code splitting, and lazy loading and all of that other stuff. Those are more  
advanced routing concepts.