<script>
    import Inner from "./components/events/Inner.svelte";
    import Outer from "./components/events/Outer.svelte";

    let m = { x: 0, y: 0 };

    function handleMousemove(event) {
        m.x = event.clientX;
        m.y = event.clientY;
    }

    function handleClick() {
        alert('no more alerts')
    }

    function handleMessage(event) {
        alert(event.detail.text);
    }
</script>

<section>
    <div on:mousemove={handleMousemove}>
        The mouse position is {m.x} x {m.y}
    </div>

    <div on:mousemove="{e => m = { x: e.clientX, y: e.clientY }}">
        The mouse position is {m.x} x {m.y}
    </div>

    <button on:click|once={handleClick}>
        Click me
    </button>

    <h3>Dispatch Events</h3>
    <Inner on:message={handleMessage}/>

    <h3>Forward Dispatch Events</h3>
    <Outer on:message={handleMessage}/>


</section>


<style>
    div { width: 100%; height: 100%; }
</style>