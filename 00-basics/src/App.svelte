<script>
    import Nested from "./components/Nested.svelte";
    let src = 'https://svelte.dev/tutorial/image.gif';
    let name = 'Rick Astley';

    let string = `this string contains some <strong>HTML!!!</strong>`;
</script>

<img {src} alt="{name} dances.">
<Nested />
<p>{@html string}</p>

<style>
    img {
        width: 100%;
    }
</style>