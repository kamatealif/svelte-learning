<script>
	import { fade, fly } from 'svelte/transition';
	let visible = $state(false);
</script>

<div class="container">
	<div class="fade-transition">
		<label>
			<input type="checkbox" bind:checked={visible} />
			visible
		</label>

		{#if visible}
			<p transition:fade>Fade In Out</p>
		{/if}
	</div>

	<hr />

	<div class="fly-transition">
		<h1>fly Transition</h1>
		<label>
			<input type="checkbox" bind:checked={visible} />
			visible
		</label>

		{#if visible}
			<p transition:fly={{ y: 200, duration: 2000 }}>Fade In Out</p>
		{/if}
	</div>
	<hr />
	<div class="fly-transition">
		<h1>In and Out Transition</h1>
		<p>
			Instead of the <kbd>transition</kbd> directive, and element can have an <kbd>in</kbd> or and
			<kbd>out</kbd> directive, or both together
		</p>
		<label>
			<input type="checkbox" bind:checked={visible} />
			visible
		</label>

		{#if visible}
			<p in:fly={{ y: 200, duration: 2000 }} out:fade>Flies in, Fades out</p>
		{/if}
	</div>
</div>

<style>
	:global(body) {
		background-color: rgb(32, 31, 31);
		color: #fff;
		font-family:
			'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana,
			sans-serif;
	}

	.container {
		max-width: 860px;
		height: 100vh;
		margin: 0 auto;
		padding: 1rem;
		border: 1px solid #ccc;
	}
</style>
