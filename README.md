# Events and Event Forwarding

### Events    
communicate child to parent component.    
here implement popup concept to practise Events. 



1. create Popup component inside 'component' folder.   

2. add basic show component logic in App comopnent with button click.

App.svelte 
```svelte
<script>
   import Popup from "./components/Popup.svelte";
   let showPopup = false;
</script>
<main>
	<button on:click={()=>{showPopup=true}} >Show Popup</button>
	{#if showPopup}
	  <Popup/>
	{/if}
</main>
```

Popup.svelte 
```svelte
<h2>PopUp Component</h2>
```

3. using custom events send message to App component to close popup

Popup.svelte 
```svelte
<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
</script>

<h2>PopUp Component</h2>
<button on:click={()=>{dispatch('close')}} >Close Popup</button>
```

get child event using 'on:close' event on child tag

App.svelte 
```svelte
<script>
   let showPopup = false;
</script>
<main>
	{#if showPopup}
	 <Popup on:close={()=>(showPopup = false)}/>
	{/if}
</main>
```

3. show in above example how to pass data to parent component.

pass data as second parameter in dispatch function in 'Popup' component.  

Popup.svelte 
```svelte
<button on:click={()=>{dispatch('close', 'samadhi')}} >Close Popup</button>
```

get child event using 'on:close' event on child tag

App.svelte 
```svelte
<script>
   let showPopup = false;
   function closePopup(event){
	  showPopup = false;
	  console.log(event.detail)
   }
</script>

<main>
	{#if showPopup}
	  <Popup on:close={closePopup}/>
	{/if}
</main>
```

# Event Forwarding   

This is needed if you want to listen to an event on a deeply nested component. 
send an event in following order.  
child event > parent > parent top


4. create another two components call 'Inner' and 'Outer' inside component folder. And place in following order as nested.   
App > Outer > Inner 

now show how to pass 'Inner' component button event to App component. 

App.svelte 
```svelte
<script>
  import Outer from "./components/Outer.svelte";
   function clickInnerButton(event){
      console.log("inner data", event.detail);
	  alert('click inner button');
   }
</script>

<main>
  <Outer on:greet={clickInnerButton}/>
</main>
```

Outer.svelte 
```svelte
<script>
    import Inner from "./Inner.svelte";
</script>

<main>
    <Inner on:greet/>
</main>
```

Inner.svelte 
```svelte
<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
</script>

<main>
    <h2>Inner Component</h2>
    <button on:click={()=>{dispatch('greet','laksahan')}} >Click</button>
</main>
```

4. create another components call 'Button' inside component folder. And place in following order as nested.   
App > Button 

now show how to pass 'Button' component button event to App component without any event dispacher.

'on:click' bind without function mean it pass to parent component as event.

Button.svelte 
```svelte
<main>
    <h2>Button Component</h2>
    <button on:click >Click Me</button>
</main>
```

App.svelte 
```svelte
<script>
   import Button from "./components/Button.svelte";
   function handleButton(event){
     alert('click button in Button component')
   }
</script>

<main>
	<Button on:click={handleButton} />
</main>
```