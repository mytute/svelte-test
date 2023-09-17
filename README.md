# List Rendering

### i
1. in script tag, define array with three string.
```js
<script>
  const names = ['Bruce', 'Clark', 'Diana'];
</script>
```  

2. in main tag, with curly braces define each tag in following way and bind values using curly braces. 
```js
<main>
  {#each names as name}
    <h2>{name}</h2>
  {/each}
</main>
```  

3. show how to use index in above list rendering   
```js
<main>
  {#each names as name, index}
    <h2>{index+1} {name}</h2>
  {/each}
</main>
```  

4. show how to render object array  
```js
<script>
  const fullNames = [
    {first:'Bruce', last: 'Wayne'},
    {first:'Clark', last: 'Kent'},
    {first:'Princess', last: 'Diana'},
  ]
</script>
<main>
  {#each fullNames as name, index}
    <h2>{index+1} {name.first} {name.last}</h2>
  {/each}
</main>
``` 

5. show how to add unique key for the above rendering list.  
add someting unique value in brakets at the end of the start of loop. here '(name)' 
```js
<main>
  {#each fullNames as name, index (name)}
    <h2>{index+1} {name.first} {name.last}</h2>
  {/each}
</main>
``` 