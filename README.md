# Vue.js Workshop

## Jesvin Jose
## Open Source Kerala 2017


## Note:

* No special requirement
* Can drop directly into the project
* Scalable
* Hot Reload (like in react) 😈

Declarative Programming

```
Bad programmers worry about the code. Good programmers worry about data structures and their relationshps - Linus Tovalds
```

If you can understand the datastrucutre you can understand the algorithm.


## Vue is reactive

* By changing the data the system will re-render its contents.
* Updating message results in having the message updated every where.

## v-cloak

* Won't show the view app until the data is mounted
* If v-cloak is not there it would show the template

## v-model

```html
<input v-model="name" />
```

If you have vue.js dev tools enabled, you can change the name via console as well. The step to do that is to run `$vm0.name = 'something'`

## methods

```js
    new Vue({
      el: '#app',
      data: {
        name: 'Arun'
      },
      methods: {
        reverse: function() {
         this.name = this.name.split("").reverse().join("");
       }
      }
    })
```

To add a method, in the methods section of our app config declare your method.

### v-on:click

To execute the above method on clicking the mutton we use the vue.js click event listener.

```html
  <button v-on:click="reverse()" >reverse</button>
```

### Note: Vue.js Lifecycle 🚲

List of callbacks that are triggered during the various stags of the view app.

Eg: mounted()


### Run a method outside vue.js in the vue.js app's context

We pass the context of the app to outside method and it would then use that context to assign
the variable.

```js
    new Vue({
      el: '#app',
      data: {
        name: 'Arun'
      },
      methods: {
        reverse: function() {
          this.name = this.name.split("").reverse().join("")
        },
        fetchName: function() {
          var that = this;
          randomName(function (name) { that.name = name })
        }
      }
    })
```

The last line of the randomName method is to pass in that result to the anonymous method we passed.

```js
    function randomName(callback){
      fetch('https://randomuser.me/api/').then( function(response){
        return response.json()
      }).then( function(json) {
        callback(json.results[0].name.first + ' ' + json.results[0].name.last)
      })
    }

  // the callback refered here is our annoynmous function.
  // Name fetched is passed into the anonymous function which assigns that name
  // to the name model of the view app
```

## Bootstrap

Bootstrap Vue.js

### v-for

For loop happens for array or list or collection

```html
  <tr v-for="item of items" :key="item.id">
   
  </tr>
```

When a new element is added to the view, vue.js will detect the change and run the extra loop to fill that.


## Questions?

* Can we use model to create & submit params?
* How to handle authenticity Token, in rails?

