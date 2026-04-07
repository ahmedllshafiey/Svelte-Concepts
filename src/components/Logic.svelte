<script>
    let count = $state(0);

    function increment() {
        count += 1;
    }

    const colors = ['red','orange','yellow','green','blue'];
    let selected = $state(colors[0]);

    let things = $state([
        {id: 1, name: 'apple'},
        {id: 2, name: 'banana'},
        {id: 3, name: 'carrot'},
        {id: 4, name: 'orange'},
        {id: 5, name: 'egg'},
    ])

    import { roll } from './utils.js';

	let promise = $state(roll());
</script>

<button onclick={increment}>
    Clicked {count} {count === 1 ? 'time' : 'times'}
</button>

{#if count > 10}
    <p>{count} is greater than 10</p>
{:else if count < 5}
    <p>{count} is less than 5</p>
{:else}
    <p>{count} is between 5 and 10</p>
{/if}

<h1 style="color: {selected}">Pick a color</h1>

<div>
    {#each colors as color(color)}
        <button
            style="background-color: {color};"
            aria-label={color}
            aria-current={selected === color}
            onclick={() => selected = color}
        >
            {color}
        </button>
    {/each}
</div>

<button onclick={()=> things.shift()}>
    Remove first item
</button>

<br>

{#each things as thing(thing.id)}
    {thing.name}
    <br>
{/each}

<br>

<button onclick={() => promise = roll()}>
	roll the dice
</button>

{#await promise}
<p>...rolling</p>
{:then number}
	<p>you rolled a {number}!</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}