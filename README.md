# Components and Props

In here automatically calculated values when dependency changes.

### Components
1. create new folder call 'components' inside 'src' folder and inside 'components' folder create new file call 'Greet.svelte'.  
```svelte
// Greet.svelte 
// no need to add main tag here.
<h2>Hello Samadhi</h2>
```

2. then import newly created component to 'App.svelte' component and see the result
```svelte
// App.svelte
<script>
  import Greet from "./components/Greet.svelte";
</script>
<main>
   <Greet/>
</main>
```

3. show how to reuse 'Greet' component by copy-past it several times
```svelte
<main>
   <Greet/>
   <Greet/>
   <Greet/>
</main>
```    

### Props   


4. show how to pass data to child component as attribute on the 'Gree' tag inside 'main' tag.
```svelte
// App.svelte
<script>
  const name = "samadhi"
</script>
<main>
	<Greet name={name} heroName="supreman"/>
	<Greet name='Diana' heroName="wonderwomen"/>
</main>
```  

5. in child component show how to receive props passing by parent and how to render that data on child component. 
```svelte
// Greet.svelte
<script>
    export let name;
    export let heroName;
</script>

<main>
    <h2>Name is {name} as {heroName}</h2>
</main>
```  

6. show how to set default value to props in child component.
```svelte
// Greet.svelte
<script>
    export let heroName = 'detault value';
</script>
```  

7. show how to spread make pass props to child component  
```svelte
// App.svelte
<script>
const obj = {
    name: 'Barry',
    heroName: 'Flash'
  }
</script>

<main>
    <Greet {...obj}/>
</main>
```  