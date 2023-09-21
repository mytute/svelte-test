<script context="module">
    let totalCount = 0;
    export function getTotalCount(){
        return totalCount;
    }
</script>

<script>
    let counter = 0;
    function clickHandler(event){
        counter ++;
        totalCount ++;
    }
</script>
<main>
    <h2>Count - {totalCount}</h2>
    <button on:click={clickHandler}>Increment</button>
</main>