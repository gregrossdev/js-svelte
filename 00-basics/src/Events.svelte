<script>
    let m = { x: 0, y: 0 };

    function handleMousemove(event) {
        m.x = event.clientX;
        m.y = event.clientY;
    }

    function handleClick() {
        alert('no more alerts')
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
</section>


<style>
    div { width: 100%; height: 100%; }
</style>