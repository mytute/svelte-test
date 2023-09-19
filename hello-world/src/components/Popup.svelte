<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();
</script>

<h2>PopUp Component</h2>
<button on:click={()=>{dispatch('close', 'samadhi')}} >Close Popup</button>