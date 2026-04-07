<script>
    let counter = $state(0);

    function increment() {
        counter += 1;
    }

    let numbers = $state([1,2,3,4]);

    function addNumber() {
        numbers.push(numbers.length + 1);
        console.log($state.snapshot(numbers));
    }

    let total = $derived(numbers.reduce((t,n)=> t + n, 0));

    let elapsed = $state(0);
    let interval = $state(1000);

    $effect(() => {
        const id = setInterval(() => {
            elapsed += 1;
        }, interval);

        return () => clearInterval(id);
    });

    import { uni } from "./Universal.svelte.js";

    function uniIncrement() {
        uni.count += 1;
    }
</script>

<h1>Counter</h1>
<button onclick={increment}>Increase</button>
<p>{counter}</p>

<h1>Add Number</h1>
<button onclick={addNumber}>Add</button>
<p>{numbers}</p>

<p>{numbers.join(" + ")} = {total}</p>

<h1>Universal Counter</h1>
<button onclick={uniIncrement}>Increase</button>
<p>{uni.count}</p>

<p>Elapsed: {elapsed}</p>
