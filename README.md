#  Component Styles

  

1. create component call 'ChildStyle' and make it 'App' component's child component. And add the h3 and h4 tags for the both components. 

App.svelte
```svelte
<script>
  import ChildStyle from "./components/ChildStyle.svelte";
</script>

<main>
   <h4>App component text</h4>
   <h3>App component global style</h3>
   <ChildStyle/>
</main>
```

ChildStyle.svelte
```svelte
<main>
    <h4>ChildStyle component text</h4>
    <h3>ChildStyle component global style</h3>
</main>
<style>

</style>
```


2. in App component, add color style for h4 tag and show it will only effect for App component and not for 'ChildStyle' component 


here only passing only string value to child component.

App.svelte
```svelte
<style>
	h4 {
	  color: orange;
	}
</style>
```

3. in ChildStyle component, add color style for h4 tag and show it will only effect for ChildStyle component and not for 'App' component.

ChildStyle.svelte
```svelte
<style>
   h4 {
     color: olivedrab;
   }
</style>
```


4. using global modifire apply global style and show it dose not matter child or parent, it will apply styles globally.  

ChildStyle.svelte
```svelte
<style>
   :global(h3){
     color: blue;
   }
</style>
```


