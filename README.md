# Event Handling

### i
1. in script tag, create new variable call count that equal to 0 with let keyword.
```js
<script>
  let count = 0;
</script>
```  

2. in main tag, create button element with click event in following way. on:click. and bind count value to button.
```js
<main>
  <button on:click={()=> count = count +1} >Count {count}</button>
</main>
```  

3. show how to execute function when click event emitted.   
```js
<script>
  let count = 0;
  function handleClick(){
    count +=1;
  }
</script>
<main>
  <button on:click={handleClick} >Count {count}</button>
</main>
```  

4. show how to pass argument to above 'handleClick' function. 
```js
<script>
  let count = 0;
  function handleClick(event, size){
    count +=size;
  }
</script>
<main>
  <button on:click={(event)=>handleClick(event, 5)} >Count {count}</button>
</main>
``` 