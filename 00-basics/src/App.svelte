<script>
    import Nested from "./components/Nested.svelte";
    import Info from "./components/Info.svelte";
    import Thing from "./components/Thing.svelte";
    import Events from "./Events.svelte";

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

    const pkg = {
        name: 'svelte',
        version: 3,
        speed: 'blazing',
        website: 'https://svelte.dev'
    };

    let user = { loggedIn: false };

    function toggle() {
        user.loggedIn = !user.loggedIn;
    }

    let x = 7;

    let cats = [
        { id: 'J---aiyznGQ', name: 'Keyboard Cat' },
        { id: 'z_AbfPXTKms', name: 'Maru' },
        { id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
    ];

    let things = [
        { id: 1, name: 'apple' },
        { id: 2, name: 'banana' },
        { id: 3, name: 'carrot' },
        { id: 4, name: 'doughnut' },
        { id: 5, name: 'egg' },
    ];

    function handleClick() {
        things = things.slice(1);
    }

    async function getRandomNumber() {
        const res = await fetch(`https://svelte.dev/tutorial/random-number`);
        const text = await res.text();

        if (res.ok) {
            return text;
        } else {
            throw new Error(text);
        }
    }

    let promise = getRandomNumber();

    function handleClickRandom() {
        promise = getRandomNumber();
    }

</script>

<!--<img {src} alt="{name} dances.">-->
<p>{@html string}</p>
<button on:click={incrementCount}>
    Clicked {count} {count === 1 ? 'time' : 'times'}
</button>
<p>{count} doubled is {doubled}</p>
<p>{numbers.join(' + ')} = {sum}</p>
<button on:click={addNumber}>
    Add a number
</button>

<Nested />
<Nested answer={42}/>
<Info {...pkg}/>

{#if user.loggedIn}
    <button on:click={toggle}>
        Log out
    </button>
{:else}
    <button on:click={toggle}>
        Log in
    </button>
{/if}

{#if x > 10}
    <p>{x} is greater than 10</p>
{:else if 5 > x}
    <p>{x} is less than 5</p>
{:else}
    <p>{x} is between 5 and 10</p>
{/if}

<h1>The Famous Cats of YouTube</h1>

<ul>
    {#each cats as { id, name }, i}
        <li><a target="_blank" href="https://www.youtube.com/watch?v={id}">
            {i + 1}: {name}
        </a></li>
    {/each}
</ul>

<button on:click={handleClick}>
    Remove first thing
</button>

{#each things as thing(thing.id)}
    <Thing name={thing.name}/>
{/each}

<button on:click={handleClickRandom}>
    generate random number
</button>

{#await promise}
    <p>...waiting</p>
{:then number}
    <p>The number is {number}</p>
{:catch error}
    <p style="color: red">{error.message}</p>
{/await}

<h2>Events</h2>
<Events />

<style>
    img {
        width: 100%;
    }
</style>