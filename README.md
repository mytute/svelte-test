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
```js 
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
```js 
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
```js 
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
```js 
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
```js 
<script>
    import { count } from '../store/stores';
</script>

<main>
    <h2>Count: {$count}</h2>
</main>
```