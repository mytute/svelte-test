<script>
    import { count, customCount } from '../store/stores';
    function increment(){
        count.update(value =>{
            return value+1;
        })
    }
</script>

<main>
    <button on:click={increment} >Increment</button>
    <button on:click={()=>{customCount.increment()}} >Custom Increment</button>
</main>