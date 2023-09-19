<script>
 let firstName = 'Bruce';
 let lastName = 'Wayne';
 $:fullName = `${firstName} ${lastName}`; // compose new variable
 $: console.log(`Fullname is ${firstName} ${lastName}`);
 $:{
  const fullName = `${firstName} ${lastName}`
  console.log(`Fullname is - ${fullName}`);
 }

 let items = [
	{id:1, title:'TV', price:100},
	{id:2, title:'Phone', price:200},
	{id:2, title:'Laptop', price:300},
 ];
 $:total = items.reduce((total,current)=>total+current.price,0);

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
  <button on:click={()=>{
	firstName= 'Samadhi';
  }} >Change First Name</button>
  <button on:click={()=>{items.push({id:2, title:'Pen', price:5})}} >Push Item</button>
  <button on:click={()=>{items = [...items, {id:2, title:'Pen', price:5}]}} >Add Item</button>
  <h2>{firstName} {lastName}</h2>
  <h2>{fullName}</h2>
  <h2>total: {total}</h2>

  <h2>Current valume {valume}</h2>
  <button on:click={()=> valume++}>Increment valume</button>
  <button on:click={()=> valume--}>Decrement valume</button>
</main>

<style>
	main {
		/* text-align: center; */
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>