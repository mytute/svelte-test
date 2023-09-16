<script>
	const name = "Samadhi";
	const channel = '<b>samadhi</b>';
	const hack = `<a href="#" onclick="alert('you have been hacked')" >Win a prize!</a>`;
</script>

<main>
	<h1>Hello {name}!</h1>
	<div>{@html channel}</div>
	<div>{@html hack}</div>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
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