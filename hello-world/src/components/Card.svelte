<script>
    export let content;
</script>

<!-- <div class="card">{content}</div> -->
<div class="card"> <slot>Default content</slot> </div>

<style>
    .card {
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
        transition: 0.2s;
        padding: 16px;
        margin-bottom: 20px;
        width: 200px;
    }
    .card:hover{
        box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
    }
</style>