<script>
    import { count } from '../store/stores';
    function reset(){
        count.set(0)
    }
</script>

<main>
    <button on:click={reset} >Reset</button>
</main>