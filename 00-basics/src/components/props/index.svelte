<script>
    import Nested from "../Nested.svelte";
    import Info from "./Info.svelte";

    const pkg = {
        name: 'svelte',
        version: 3,
        speed: 'blazing',
        website: 'https://svelte.dev'
    };

</script>

<section>
    <h3>Declaring Props</h3>
    <Nested answer={42}/>

    <h3>Default Props</h3>
    <Nested answer={42}/>
    <Nested/>

    <h3>Spread Props</h3>
    <Info {...pkg}/>
</section>


