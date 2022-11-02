<script>
    import Intro from "./components/introduction/index.svelte"
    import React from "./components/reactivity/index.svelte"
    import Props from "./components/props/index.svelte"
    import Logic from "./components/logic/index.svelte"
    import Events from "./components/events/index.svelte";
    import Bindings from "./components/bindings/index.svelte"
</script>

<main>
    <h2>Introduction</h2>
    <Intro />

    <h2>Reactivity</h2>
    <React />

    <h2>Props</h2>
    <Props />

    <h2>Logic</h2>
    <Logic />

    <h2>Events</h2>
    <Events />

    <h2>Bindings</h2>
    <Bindings />
</main>


<style>
    main {
        margin: 0 auto;
        padding: 0.5rem 1rem;
        width: 600px;
    }
    h2 {
        width: 80%;
        border-bottom: #475569 solid medium;
    }
</style>