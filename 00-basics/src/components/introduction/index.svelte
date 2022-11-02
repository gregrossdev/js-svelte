<script>
    import Nested from "./Nested.svelte";
    let name = "World!!"
    let src = 'https://svelte.dev/tutorial/image.gif';
    let imgName = 'Rick Astley';

    let string = `this string contains some <strong>HTML!!!</strong>`;


</script>

<section>
    <h3>Adding Data</h3>
    <p>Hello {name}!</p>

    <h3>Dynamic Attributes</h3>
    <!-- {src} is short for src={src} -->
    <!--<img {src} alt="{imgName} dancing">-->

    <h3>Styling</h3>
    <span>This is a styled line.</span>

    <h3>Nested Components</h3>
    <Nested />

    <h3>HTML Rendering</h3>
    <p>{@html string}</p>
</section>


<style>
    span {
        font-family: 'Comic Sans MS', cursive;
        font-size: 1.2em;
    }
    img {
        width: 100%;
    }
</style>