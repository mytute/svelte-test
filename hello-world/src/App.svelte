<script>
  import Card from "./components/Card.svelte";
</script>

<main>
	<Card> Card Content </Card>
	<Card> <h2>Card Content</h2> </Card>
	<Card/>
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