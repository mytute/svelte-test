# Contex api

context provides a way to pass data through the component tree without having to pass proos down manually at every level.

* set a context value.
* get the context value.


1. create ComponentC, ComponentE, ComponentF inside 'component' folder in 'src' folder.  

2. Then link created component in following order as nested component.   

* App > ComponentC > ComponentE > ComponentF

App.svelte 
```svelte
<script>
  import ComponentC from "./components/ComponentC.svelte";
  const userName = 'Samadhi';
</script>
<main>
	<h2>App component username - {userName}</h2>
	<ComponentC />
</main>
```

ComponentC.svelte 
```svelte
<script>
    import ComponentE from "./ComponentE.svelte";
</script>
<h2>Child C Component</h2>
<ComponentE />
```

ComponentE.svelte 
```svelte
<script>
    import ComponentF from "./ComponentF.svelte";
</script>

<h2>Child E Component</h2>
<ComponentF />
```

ComponentF.svelte 
```svelte
<script>
</script>

<h2>Child F Component</h2>
<h2>Child F userName - {userName}</h2>
```

3. show how to pass 'App' component 'userName' variable to 'ComponentC'

App.svelte 
```svelte
<script>
  import { setContext } from "svelte";
  const userName = 'Samadhi';
  setContext('username-context', userName);
</script>
```

ComponentF.svelte 
```svelte
<script>
    import { getContext } from "svelte";
    const userName = getContext('username-context');
</script>

<h2>Child F Component</h2>
<h2>Child F userName - {userName}</h2>
```