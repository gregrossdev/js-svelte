<script>
    import Inner from "./Inner.svelte";
    import Outer from "./Outer.svelte";
    import CustomButton from "./CustomButton.svelte";

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

    function handleClickButton() {
        alert('Button Clicked');
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

    <h3>Forward DOM Events</h3>
    <CustomButton on:click={handleClickButton}/>
</section>


<style>
    div { width: 100%; height: 100%; }
</style>