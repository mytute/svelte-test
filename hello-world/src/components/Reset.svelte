<script>
    import { count, customCount } from '../store/stores';
    function reset(){
        count.set(0)
    }
</script>

<main>
    <button on:click={reset} >Reset</button>
    <button on:click={()=>{customCount.reset()}} >Custom Reset</button>
</main>