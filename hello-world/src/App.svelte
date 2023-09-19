<script>
  import Greet from "./components/Greet.svelte";
  const name = "samadhi"
  const obj = {
	name: 'Barry',
	heroName: 'Flash'
  }
</script>

<main>
	<Greet name={name} heroName="supreman"/>
	<Greet name='Diana' heroName="wonderwomen"/>
	<Greet {...obj}/>
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