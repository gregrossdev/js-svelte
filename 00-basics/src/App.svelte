<script>
    import Nested from "./components/Nested.svelte";
    let src = 'https://svelte.dev/tutorial/image.gif';
    let name = 'Rick Astley';

    let string = `this string contains some <strong>HTML!!!</strong>`;

    let count = 0;
    $: doubled = count * 2;

    $: if (count >= 10) {
        alert('count is dangerously high!');
        count = 9;
    }

    function incrementCount() {
        count += 1;
    }

    // $: console.log('the count is ' + count);
    // $: {
    //     console.log('the count is ' + count);
    //     alert('I SAID THE COUNT IS ' + count);
    // }

    let numbers = [1, 2, 3, 4];

    function addNumber() {
        numbers = [...numbers, numbers.length + 1];
    }

    $: sum = numbers.reduce((t, n) => t + n, 0);

</script>

<!--<img {src} alt="{name} dances.">-->
<Nested answer={42}/>
<p>{@html string}</p>
<button on:click={incrementCount}>
    Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
<p>{count} doubled is {doubled}</p>
<p>{numbers.join(' + ')} = {sum}</p>

<button on:click={addNumber}>
    Add a number
</button>

<style>
    img {
        width: 100%;
    }
</style>