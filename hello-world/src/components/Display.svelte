<script>
    import { count, customCount } from '../store/stores';
    $:console.log($customCount)
</script>

<main>
    <h2>Count: {$count}</h2>
    <h2>The custom count is {$customCount}</h2>
</main>