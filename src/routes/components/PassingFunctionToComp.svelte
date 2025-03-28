<script>
	let count = $state(0);

	function increment() {
		count += 1;
	}

	function decrement() {
		count -= 1;
	}
</script>

{#snippet Stepper(increment, decrement)}
	<button onclick={decrement}>-1</button>
	<button onclick={increment}>+1</button>
{/snippet}

<p>The current value is {count}</p>
{@render Stepper(increment, decrement)}
