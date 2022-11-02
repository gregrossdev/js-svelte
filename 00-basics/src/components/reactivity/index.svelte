<script>
    // assignments
    let count = 0;
    function incrementCount() {
        count += 1;
    }

    // declarations
    count = 0;
    $: doubled = count * 2;
    function handleClick() {
        count += 1;
    }

    // statements
    count = 0;
    $: if (count >= 10) {
        alert('count is dangerously high!');
        count = 9;
    }
    function handleClick01() {
        count += 1;
    }
/*
    $: console.log('the count is ' + count);
    $: {
        console.log('the count is ' + count);
        alert('I SAID THE COUNT IS ' + count);
    }
*/

    // mutations
    let numbers = [1, 2, 3, 4];
    function addNumber() {
        numbers = [...numbers, numbers.length + 1];
    }
    $: sum = numbers.reduce((t, n) => t + n, 0);

</script>

<section>
    <h3>Assignments</h3>
    <button on:click={incrementCount}>
        Clicked {count} {count === 1 ? 'time' : 'times'}
    </button>

    <h3>Declarations</h3>
    <button on:click={handleClick}>
        Clicked {count} {count === 1 ? 'time' : 'times'}
    </button>
    <p>{count} doubled is {doubled}</p>

    <h3>Statements</h3>
    <button on:click={handleClick01}>
        Clicked {count} {count === 1 ? 'time' : 'times'}
    </button>

    <h3>Mutations</h3>
    <p>{numbers.join(' + ')} = {sum}</p>
    <button on:click={addNumber}>
        Add a number
    </button>

</section>


