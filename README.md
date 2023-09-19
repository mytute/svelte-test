# Reactive Declarations and Reactive Statements

In here automatically calculated values when dependency changes.

### Reactive Declarations
1. in script tag, define two variable call 'firstName' and 'lastName'. and using reactive declaration make new variable of both above values.  
```svelte
<script>
 let firstName = 'Bruce';
 let lastName = 'Wayne';
 $:fullName = `${firstName} ${lastName}`; // compose new variable
</script>
```

2. in main tag, define above normal and reactive delaration in h2 tab and see the result
```svelte
<main>
  <h2>{firstName} {lastName}</h2>
  <h2>{fullName}</h2>
</main>
```  

3. add the button in main tag and when onclick event change 'firstName' variable to another name and see how svelte update values when dependency changed.   
```svelte
<main>
  < <button on:click={()=>{
	firstName= 'Samadhi';
  }} >Change First Name</button>
</main>
```  

4. in script tag, create new object-array variable call 'items'. And calculate total price and store it in Reactive-Declarative way. after that show total result in main tag
```svelte
<script>
 let items = [
	{id:1, title:'TV', price:100},
	{id:2, title:'Phone', price:200},
	{id:2, title:'Laptop', price:300},
 ];
 $:total = items.reduce((total,current)=>total+current.price,0);
</script>
<main>
  <h2>total: {total}</h2>
</main>
```

5. show mutation will not cause a rerender and reactive system works based on assignment. 

add a new button and in it's event add the new item to items array.    

```svelte
<main>
  <button on:click={()=>{items.push({id:2, title:'Pen', price:5})}} >Push Item</button>
  <button on:click={()=>{items = [...items, {id:2, title:'Pen', price:5}]}} >Add Item</button>
</main>
```

### Reactive Statements    

6. in the script tag, add console.log statement as reactive statement. and see when change name button click it will create new console.log in the browser with new value.

```svelte
<script>
 $: console.log(`Fullname is ${firstName} ${lastName}`);
</script>
```

7. show Reactive Statements can make inside curly braces and make more statement to it.   
```svelte
<script>
 $:{
  const fullName = `${firstName} ${lastName}`
  console.log(`Fullname is ${fullName}`);
 }
</script>
```

7. show using Reactive Statements how to handdle volume control max and min .   
```svelte
<script>
 $:if(valume < 0){
	alert(`Can't go lower`);
	valume = 0;
 }else if(valume>20){
	alert(`Can't go higher`);
	valume = 20;
 }
 let valume = 0;
</script>
<main>
  <h2>Current valume {valume}</h2>
  <button on:click={()=> valume++}>Increment valume</button>
  <button on:click={()=> valume--}>Decrement valume</button>
</main>

```