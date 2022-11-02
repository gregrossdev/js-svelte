<script>
    import Thing from "../Thing.svelte";

    let user = { loggedIn: false };

    function toggle() {
        user.loggedIn = !user.loggedIn;
    }

    let x = 7;

    // each
    let cats = [
        { id: 'J---aiyznGQ', name: 'Keyboard Cat' },
        { id: 'z_AbfPXTKms', name: 'Maru' },
        { id: 'OUtn3pvWmpg', name: 'Henri The Existential Cat' }
    ];

    // each keyed
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

    // await
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

<section>
    <h3>If Blocks</h3>
    {#if user.loggedIn}
        <button on:click={toggle}>
            Log out
        </button>
    {/if}

    {#if !user.loggedIn}
        <button on:click={toggle}>
            Log in
        </button>
    {/if}

    <h3>Else Blocks</h3>
    {#if user.loggedIn}
        <button on:click={toggle}>
            Log out
        </button>
    {:else}
        <button on:click={toggle}>
            Log in
        </button>
    {/if}

    <h3>Else-if Blocks</h3>
    {#if x > 10}
        <p>{x} is greater than 10</p>
    {:else if 5 > x}
        <p>{x} is less than 5</p>
    {:else}
        <p>{x} is between 5 and 10</p>
    {/if}

    <h3>Each Blocks</h3>
    <h4>The Famous Cats of YouTube</h4>
    <ul>
        {#each cats as { id, name }, i}
            <li><a target="_blank" href="https://www.youtube.com/watch?v={id}">
                {i + 1}: {name}
            </a></li>
        {/each}
    </ul>

    <h3>Keyed Each Blocks</h3>
    <button on:click={handleClick}>
        Remove first thing
    </button>
    {#each things as thing(thing.id)}
        <Thing name={thing.name}/>
    {/each}

    <h3>Await Blocks</h3>
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
</section>












