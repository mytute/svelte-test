<script>
	const names = ['Bruce', 'Clark', 'Diana'];
	const fullNames = [
		{first:'Bruce', last: 'Wayne'},
		{first:'Clark', last: 'Kent'},
		{first:'Princess', last: 'Diana'},
	];
</script>

<main>
 {#each names as name, index}
    <h2>{index+1} {name}</h2>
 {/each}
 {#each fullNames as name, index (name.first)}
    <h2>{index+1} {name.first} {name.last}</h2>
  {/each}
</main>

<style>
	main {
		text-align: center;
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