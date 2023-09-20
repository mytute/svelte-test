<script>
  import Card from "./components/Card.svelte";
  import Card2 from "./components/Card2.svelte";
  import NameList from "./components/NameList.svelte";
</script>

<main>
	<Card> Card Content </Card>
	<Card> <h2>Card Content</h2> </Card>
	<Card2>
		<div slot="header"> <h2>this is header</h2></div>
		<div slot="content"> <img src="https://picsum.photos/200" alt=""> </div>
		<!-- <div slot="footer"> <button>View details</button></div> -->
	</Card2>
	<NameList>
		<h3 slot='hero' let:firstName let:lastName >
			{firstName} {lastName}
		</h3>
	</NameList>
	<NameList>
		<h3 slot='hero' let:firstName let:lastName >
			{lastName} {firstName} 
		</h3>
	</NameList>
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