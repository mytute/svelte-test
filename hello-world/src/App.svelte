<script>
   import Popup from "./components/Popup.svelte";
   import Outer from "./components/Outer.svelte";
   import Button from "./components/Button.svelte";
   let showPopup = false;
   function closePopup(event){
	  showPopup = false;
	  console.log(event.detail)
   }
   function clickInnerButton(event){
      console.log("inner data", event.detail);
	  alert('click inner button');
   }
   function handleButton(event){
     alert('click button in Button component')
   }
</script>

<main>
	<button on:click={()=>{showPopup=true}} >Show Popup</button>
	{#if showPopup}
	  <Popup on:close={closePopup}/>
	{/if}
	<Outer on:greet={clickInnerButton}/>
	<Button on:click={handleButton} />
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