<script>
    import { count } from '../store/stores';
    function increment(){
        count.update(value =>{
            return value+1;
        })
    }
</script>

<main>
    <button on:click={increment} >Increment</button>
</main>