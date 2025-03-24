<script>
	let a = $state(1);
	let b = $state(2);
</script>

<form action="">
	<div>
		<input type="number" min="0" max="100" bind:value={a} />
		<input type="range" min="0" max="100" bind:value={a} />
	</div>
	<div>
		<input type="number" min="0" max="100" bind:value={b} />
		<input type="range" min="0" max="100" bind:value={b} />
	</div>
</form>

<p>{a} + {b} = {a + b}</p>
