<script>
    import Nested from "./components/Nested.svelte";
    let src = 'https://svelte.dev/tutorial/image.gif';
    let name = 'Rick Astley';

    let string = `this string contains some <strong>HTML!!!</strong>`;

    let count = 0;
    $: doubled = count * 2;

    function incrementCount() {
        count += 1;
    }
</script>

<!--<img {src} alt="{name} dances.">-->
<Nested />
<p>{@html string}</p>
<button on:click={incrementCount}>
    Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
<p>{count} doubled is {doubled}</p>

<style>
    img {
        width: 100%;
    }
</style>