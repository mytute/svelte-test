<script>
    import { count, customCount } from '../store/stores';
    function decrement(){
        count.update(value =>{
            return value-1;
        })
    }
</script>

<main>
    <button on:click={decrement} >Decrement</button>
    <button on:click={()=>{customCount.decrement()}} >Custom Decrement</button>
</main>