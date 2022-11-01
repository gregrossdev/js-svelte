<script>
    let src = 'https://svelte.dev/tutorial/image.gif';
    let name = 'Rick Astley';
    import Nested from "./components/Nested.svelte";
</script>

<img {src} alt="{name} dances.">
<Nested />

<style>
    img {
        width: 100%;
    }
</style>