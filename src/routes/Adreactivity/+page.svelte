<script>
	import { SvelteDate } from 'svelte/reactivity';
	let date = new SvelteDate();

	const pad = (n) => (n < 10 ? '0' + n : n);

	$effect(() => {
		const interval = setInterval(() => {
			date.setTime(Date.now());
		}, 1000);

		return () => {
			clearInterval(interval);
		};
	});
	const MAX_SIZE = 200;

	class Box {
		width = $state(0);
		height = $state(0);
		area = $derived(this.width * this.height);

		constructor(width, height) {
			this.width = width;
			this.height = height;
		}

		embiggen(amount) {
			this.width += amount;
			this.height += amount;
		}
	}

	const box = new Box(100, 100);
</script>
<nav>
	<ul>
		<li><a href="Adreactivity/gettersandsetters">getters and setters</a></li>
	</ul>
</nav>
<div class="container">
	<div>
		<h1>Reactive Classes</h1>
		<label>
			<input type="range" bind:value={box.width} min={0} max={MAX_SIZE} />
			{box.width}
		</label>

		<label>
			<input type="range" bind:value={box.height} min={0} max={MAX_SIZE} />
			{box.height}
		</label>

		<button onclick={() => box.embiggen(10)}>embiggen</button>

		<hr />

		<div class="box" style:width="{box.width}px" style:height="{box.height}px">
			{box.area}
		</div>

		<hr />

		<div>
			<h1>Reactive Date</h1>
			<p>The time is {date.getHours()}:{pad(date.getMinutes())}:{pad(date.getSeconds())}</p>
		</div>
	</div>
</div>

<style>
	nav{
		background: hsl(15 100 50);
		padding: 1rem;
		color: white;
		margin-bottom: 1rem;

	}

	nav ul{
		list-style: none;
		padding: 0;
		margin: 0;
		display: flex;
		gap: 1rem;
	}
	nav li{
		display: inline-block;
	}
	nav li:hover{
		text-decoration: underline;
	}
	nav li:active{
		text-decoration: underline;
	}
	nav li:focus{
		text-decoration: underline;
	}
	nav li:focus-within{
		text-decoration: underline;
	}
	nav a{
		color: white;
		text-decoration: none;

	}

	.container {
		max-width: 860px;
		height: 100%;
		margin: 0 auto;
		padding: 1rem;
		border: 1px solid #ccc;
		display: flex;
		flex-direction: column;
	}
	.container h1 {
		margin: 0;
	}
	label {
		display: flex;
		align-items: center;
	}

	hr {
		margin: 1em 0;
		border: none;
		border-bottom: 1px solid #888;
	}

	.box {
		background: radial-gradient(at 25% 25%, hsl(15 100 60), hsl(15 100 50));
		border-radius: 2px;
		filter: drop-shadow(0 0 10px hsl(15 100 50 / 0.3));
		display: flex;
		align-items: center;
		justify-content: center;
		overflow: hidden;
	}
</style>
