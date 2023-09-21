#  Module Context

sometime we need to share component current data between componet. for that we can use Module Context 

1. create new component call 'Counter' and make increment funtionility by click evnet. And add 3 'Counter' tag in to 'App' component. and show they make increment individually 

Counter.svelte
```svelte
<script>
    let counter = 0;
    function clickHandler(event){
        counter ++;
    }
</script>
<main>
    <h2>Count - {counter}</h2>
    <button on:click={clickHandler}>Increment</button>
</main>
```

2. in 'Counter' component make another script tag and make it "context='module'". 
make 'totalCount' varialbe to calculate total increment.

Counter.svelte
```svelte
<script context="module">
    let totalCount = 0;
    export function getTotalCount(){
        return totalCount;
    }
</script>

<script>
    let counter = 0;
    function clickHandler(event){
        counter ++;
        totalCount ++;
    }
</script>
<main>
    <h2>Count - {counter}</h2>
    <button on:click={clickHandler}>Increment</button>
</main>
```

3. in App component impoirt 'getTotalCount' function and fire it when click the button. because this value not update when componnet rerender.

App.svelte
```svelte
<script>
  import Counter, { getTotalCount }  from "./components/Counter.svelte";
</script>

<main>
	<button on:click={()=>{alert(getTotalCount())}} >Alert total count</button>
   <Counter/>
   <Counter/>
   <Counter/>
</main>
```

4. in 'Counter' component show if we use 'totalCount' variable instead of 'counter' it will not update the dom. show but counting by click 'Add total count' button on 'App' component.  

Counter.svelte
```svelte
<script context="module">
    let totalCount = 0;
    export function getTotalCount(){
        return totalCount;
    }
</script>

<script>
    let counter = 0;
    function clickHandler(event){
        counter ++;
        totalCount ++;
    }
</script>
<main>
    <h2>Count - {totalCount}</h2>
    <button on:click={clickHandler}>Increment</button>
</main>
```