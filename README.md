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
