#  Dynamic Components

  do following task without dynamic components and with dynamic component.  

  task: 
  show the 'Tab A', 'Tab B', 'Tab C' content when click tab button   

### with if/else

1. create three components call 'TabA', 'TabB', 'TabC'  inside components folder. And make them child to 'App' component.

2. in App component add 3 buttons to each tab and show only selected content using if/else. 

App.svelte
```svelte
<script>
  import TabA from "./components/TabA.svelte";
  import TabB from "./components/TabB.svelte";
  import TabC from "./components/TabC.svelte";

  let activeTab = 'TabA'
</script>

<main>
	<button on:click={()=>{activeTab='TabA'}}>Tab A</button>
	<button on:click={()=>{activeTab='TabB'}}>Tab B</button>
	<button on:click={()=>{activeTab='TabC'}}>Tab C</button>
    {#if activeTab === 'TabA'}
	<TabA/>
	{/if}
	{#if activeTab === 'TabB'}
	<TabB/>
	{/if}
	{#if activeTab === 'TabC'}
	<TabC/>
	{/if}

</main>
```


### with Dynamic Components  

3. show above same baheviour with 'svelte:component' special elements

App.svelte
```svelte
<script>
  import TabA from "./components/TabA.svelte";
  import TabB from "./components/TabB.svelte";
  import TabC from "./components/TabC.svelte";

  let activeTab = TabA
</script>

<main>
	<button on:click={()=>{activeTab=TabA}}>Tab A</button>
	<button on:click={()=>{activeTab=TabB}}>Tab B</button>
	<button on:click={()=>{activeTab=TabC}}>Tab C</button>

	<svelte:component this={activeTab} ></svelte:component>

</main>

```

### Special Elements 

svelte:component - for dynamic components.  
svelte:sefl - Allows a components to contain itself recursively.  
svelte:window - Add event listeners to the window object.
svlete:body - listen for events that fire on the document body 
svelte:head - insert elements inside the <head> of your document.  
svelte:options - Specify compiler options.








1. onMount hook   

The onMount function schedules the passed in callback to run as soon as the component has been mounted to the DOM.

If you return a function from the callback function, that function will be called when the component is unmounted. 

App.svelte
```svelte
<script>
	import { onMount } from "svelte";
	onMount(async ()=>{
		// call api here 
	})
</script>
```

2. onDestroy hook   

This hook shcedules a callback to run immediately before the component is unmounted.  

You could perform tasks like clearing timers and removing event listeners.   

'onMount' does not render inside a server-side component where as 'onDestroy' does.    

App.svelte
```svelte
<script>
	import { onDestroy } from "svelte";

	const interval = setInterval(()=>{}, 1000);

	onDestroy(()=>{
		clearInterval(interval)
	});

</script>
```

3,4 beforeUpdate & afterUpdate hook.   

beforeUpdate hook schedules a callback to run immediately before the component is updated.   

afterUpdate hook schedules a callback to run immediately after the component has been updated. 

They can be used to access the existing DOM before and after an update.    


App.svelte
```svelte
<script>
	import { beforeUpdate, afterUpdate } from "svelte";

	let div, autoscroll;
	beforeUpdate(()=>{
    // can access dom
		autoscroll =div && (div.offsetHeight + div.scrollTop) > (div.scrollHeight -20);
	})

	afterUpdate(()=>{
    // can access dom
		if(autoscroll) div.scrollTo(0, div.scrollHeight);
	})
</script>
```

5. tick hook    

Returns a promise that resolves once any pending state changes have been applied.   

The tick function is unlike other lifecycle function in that you can call it any time and not just when the component first initializes.  

It does help when you want to run some code after pending changes have been applied to the DOM.

App.svelte
```svelte
<script>
	import { tick } from "svelte";

	await tick();
</script>
```


### Http request

6. create new component call 'PostList' in component folder and set it as child of 'App' component.  

PostList.svelte
```svelte
<script>
    import { onMount } from "svelte";

    let posts = [];

    onMount(async()=>{
       const response = await fetch('https://jsonplaceholder.typicode.com/posts')
       posts = await response.json();
       console.log(posts);
    })
</script>

<main>
    {#each posts as post (post.id)}
      <h3>{post.id} {post.title} </h3>
      <p>{post.body}</p>
      <hr>
    {/each}
</main>
```

7. add loading indicator if posts count is empty(loading)
PostList.svelte
```svelte
<main>
    {#each posts as post (post.id)}
      <h3>{post.id} {post.title} </h3>
      <p>{post.body}</p>
      <hr>
      {:else} 
      <p>Loading</p>  
    {/each}
</main>
```

### Bind this

show how to focus on input element when component loaded using 'onMount' hook 

8. create new component call 'AutoFocus' inside component folder and make it child of 'App' component. 

9. using 'bind:this' store DOM to variable call 'inputRef' that we define in script tag.

AutoFocus.svelte
```svelte
<script>
  import { onMount } from "svelte";
  let inputRef

  onMount(()=>{
    inputRef.focus();
  })
</script>

<main>
    <input type="text" bind:this={inputRef} >
</main>
```