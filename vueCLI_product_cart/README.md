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