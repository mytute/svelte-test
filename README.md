# Conditional Rendering

### if condition
1. in script tag, define variable call 'num' equal to 0 
```js
<script>
  const num = 5;
</script>
```  

2. in main tag, create if condition inside curly braces with '#if' symbol and end with '/if' symbol.     
```js
<main>
  {#if num === 0} 
    <h2> The number is zero </h2> // this tag showing if condition true
  {/if}  
</main>
```  

### if, else and if else conditions

3. show how to use if, else and if else conditions to check is number equal to zero or negative or positive or not a number.

```js
<main>
  {#if num === 0} 
    <h2> The number is zero </h2> 
  {:else if num < 0 }
    <h2> The number is negative </h2> 
  {:else if num > 0 }
    <h2> The number is positive </h2> 
  {:else }
    <h2> Not a number </h2> 
  {/if}  
</main>
```    