<script>
    let src = 'https://svelte.dev/tutorial/image.gif';
    let name = 'Rick Astley';
</script>

<img {src} alt="{name} dances.">

<style>
    img {
        width: 100%;
    }
</style>