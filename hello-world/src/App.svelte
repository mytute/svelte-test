<script>
	import { onMount } from "svelte";
	import { onDestroy } from "svelte";
	import { beforeUpdate, afterUpdate } from "svelte";
	import { tick } from "svelte";
	import PostList from "./components/PostList.svelte";
	import AutoFocus from "./components/AutoFocus.svelte";

	onMount(async ()=>{
		console.log("onMount");
		// call api here
	});

	const interval = setInterval(()=>{}, 1000);

	onDestroy(()=>{
		console.log("onDestroy");
		clearInterval(interval)
	});

	let div, autoscroll;
	beforeUpdate(()=>{
		console.log("beforeUpdate");
		autoscroll =div && (div.offsetHeight + div.scrollTop) > (div.scrollHeight -20);
	})

	afterUpdate(()=>{
		console.log("afterUpdate");
		if(autoscroll) div.scrollTo(0, div.scrollHeight);
	})

</script>

<main>
	<PostList/>
	<AutoFocus/>

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