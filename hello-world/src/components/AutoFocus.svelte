<script>
  import { onMount } from "svelte";
  let inputRef

  onMount(()=>{
    inputRef.focus();
  })
</script>

<main>
    <input type="text" bind:this={inputRef} >
</main>