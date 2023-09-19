<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
</script>

<main>
    <h2>Inner Component</h2>
    <button on:click={()=>{dispatch('greet','laksahan')}} >Click</button>
</main>