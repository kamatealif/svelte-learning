<script>
	import { fade, fly } from 'svelte/transition';
	let visible = $state(false);
	let status = $state('waiting...');

	import { slide } from 'svelte/transition';

	let items = ['one', 'two', 'three', 'four', 'five', 'six', 'seven', 'eight', 'nine', 'ten'];

	let showItems = $state(true);
	let i = $state(5);
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

	<hr />
	<div class="fly-transition">
		<h1>Transition Events</h1>
		It can be useful to know when transitions are beginning and ending. Svelte dispatches events that
		you can listen to like any other DOM event:
		<label>
			<input type="checkbox" bind:checked={visible} />
			visible
		</label>

		{#if visible}
			<p
				transition:fly={{ y: 200, duration: 2000 }}
				onintrostart={() => (status = 'intro started')}
				onoutrostart={() => (status = 'outro started')}
				onintroend={() => (status = 'intro ended')}
				onoutroend={() => (status = 'outro ended')}
			>
				Flies in, Fades out
			</p>
		{/if}
		<p>{status}</p>
	</div>
	<hr />
	<div class="fly-transition">
		<h1>Global Transitions</h1>

		<label>
			<input type="checkbox" bind:checked={showItems} />
			show list
		</label>

		<label>
			<input type="range" bind:value={i} max="10" />
		</label>

		{#if showItems}
			{#each items.slice(0, i) as item}
				<div transition:slide|global class="global-transition">
					{item}
				</div>
			{/each}
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
		height: 100%;
		margin: 0 auto;
		padding: 1rem;
		border: 1px solid #ccc;
	}
	kbd {
		background-color: #cccccc36;
		padding: 2px 4px;
		border-radius: 4px;
	}
	.global-transition {
		padding: 0.5em 0;
		border-top: 1px solid #eee;
	}
</style>
