<script>
	import { fade } from 'svelte/transition';

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
