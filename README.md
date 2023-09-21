#  Store

Svelte Store similler to Redux in React. 

Context api can solve the same problem. But Store helps to organize code much better way and state change more predictable since Store expose the method that can alter state value.

### Store - Counter example 

for undertand we not implement counter in single component but for each feature (Increment, Decrement, Rest, Display) we create diffrent components. 


1. create folder call 'store' in 'src' folder and inside 'store' folder create file call 'stores.js'

stores.js
```js 
import { writable } from 'svelte/store';
export const count = writable();
```

2. create new component call 'Display' for display store 'count' value and make subscribe the 'count' store. And make unsubscribe the count store using 'onDestroy' hook

Display.svelte
```svelte 
<script>
    import { onDestroy } from 'svelte';
    import { count } from '../store/stores';
    let counter;
    const unsubscribe = count.subscribe((value) => {
        console.log(value);
        counter = value;
    });
    onDestroy(unsubscribe)
</script>

<main>
    <h2>Count: {counter}</h2>
</main>
```

3. create new component call 'Increment' to update count store value when click 'Increment' button on this 'Increment' component.

Increment.svelte
```svelte 
<script>
    import { count } from '../store/stores';
    function increment(){
        count.update(value =>{
            return value+1;
        })
    }
</script>

<main>
    <button on:click={increment} >Increment</button>
</main>
```

4. create new component call 'Decrement' to update count store value when click 'Decrement' button on this 'Decrement' component.

Decrement.svelte
```svelte 
<script>
    import { count } from '../store/stores';
    function decrement(){
        count.update(value =>{
            return value-1;
        })
    }
</script>

<main>
    <button on:click={decrement} >Decrement</button>
</main>
```

5. create new component call 'Reset' to set count store value 0 when click 'Reset' button on this 'Reset' component.
Reset.svelte
```svelte 
<script>
    import { count } from '../store/stores';
    function reset(){
        count.set(0)
    }
</script>

<main>
    <button on:click={reset} >Reset</button>
</main>
```

6. trick: in Display component instead of unsubscription you can use '$' symbol before 'count' variable for auto unsubscribe count store.   

Display.svelte
```svelte 
<script>
    import { count } from '../store/stores';
</script>

<main>
    <h2>Count: {$count}</h2>
</main>
```

### Readable Stores   

Readable Stores not allow to update value from other components.    
as a example for Readable store make time component.   

7. add 'readable' time store in 'store.js' file   

```js 
import { readable } from 'svelte/store';

export const time = readable(new Date(), set =>{
    const interval = setInterval(()=>{
        set(new Date())
    }, 1000);

    return function(){
        clearInterval(interval);
    }
})
```

8. make new component call 'Timer' and dispaly 'time' store value in 'Timer' component. when you '$' with store the no need to subscribe/unsubscribe.     

Timer.svelte
```svelte 
<script>
    import { time } from '../store/stores';
    const dateFormatter = new Intl.DateTimeFormat('en',{
        hour12:true,
        hour: 'numeric',
        minute: '2-digit',
        second: '2-digit'
    })
</script>

<main>
  <h2>The time is {dateFormatter.format($time)}</h2>
</main>
```



### Derived Stores 

store who is value is base on the value no more other store is called 'Derived' store.

9. show duration of seconds that page init. 
here count of seconds should update when store 'time' value changed. for that we are using 'derived'

```js 
import { readable, derived } from 'svelte/store';

export const time = readable(new Date(), set =>{
    const interval = setInterval(()=>{
        set(new Date())
    }, 1000);

    return function(){
        clearInterval(interval);
    }
});

const start = new Date();
export const elapsedTime = derived(time, $time => {
    return Math.round(($time - start)/1000);
})
```

Timer.svelte
```svelte 
<script>
    import { elapsedTime } from '../store/stores';
</script>

<main>
  <h2>You have been viewing this page for {$elapsedTime} </h2>
</main>
```

### Custom Stores 

10. create 'createCount' function that return state change function. in this way we no need to handdle state change logic in the component.   
store.js
```js 
function createCount(){
    const { subscribe, set, update } = writable(0);
    return {
        subscribe,
        increment: (size=1)=> update((n)=> n+size),
        decrement: (size=1)=> update((n)=> n-size),
        reset: ()=> set(0),
    }
}
export const customCount = createCount();
```

11. import 'customCount' where you need to import and call it's function to change state.   
in following code show call customCount function in above Increment component.  

Increment.svelte
```svelte 
<script>
    import {  customCount } from '../store/stores';
</script>

<main>
    <button on:click={()=>{customCount.increment()}} >Custom Increment</button>
</main>
```

12. show how to use 'customCount' component to dispaly it's value in 'Timer' component.   

Timer.svelte
```svelte 
<script>
    import { elapsedTime } from '../store/stores';
</script>

<main>
  <h2>You have been viewing this page for { $elapsedTime } </h2>
</main>
```