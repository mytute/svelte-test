<script>
    const names = [
        {fitstName: 'samadhi', lastName: 'laksahan'},
        {fitstName: 'thi', lastName: 'pasi'},
        {fitstName: 'mala', lastName: 'rath'},
    ];
</script>


<main>
    {#each names as name (name)}
      <slot name="hero" firstName={name.fitstName} lastName={name.lastName}/>
    {/each}
</main>

<style>

</style>