<script lang="ts">
	import AsyncMasterpiece from './components/AsyncMasterpiece.svelte';
	// import Card from './Card.svelte';
	import DomEvents from './components/DomEvents.svelte';
	import EachLoops from './components/EachLoops.svelte';
	import Header from './components/Header.svelte';
	import InlineHandler from './components//InlineHandler.svelte';
	import Thing from './components/Thing.svelte';
	import PassingFunctionToComp from './components/PassingFunctionToComp.svelte';
	import Spread from './components/Spread.svelte';

	// import horn from './components/horn.mp3';
	import TextInput from './components/TextInput.svelte';
	import NumericInput from './components/NumericInput.svelte';
	import CheckBoxInput from './components/CheckBoxInput.svelte';
	import SelectBinding from './components/SelectBinding.svelte';
	import TextAreaBinding from './components/TextAreaBinding.svelte';
	import ClassAttributes from './components/ClassAttributes.svelte';
	import StyleAttribute from './components/StyleAttribute.svelte';
	import ComponenetStyles from './components/ComponenetStyles.svelte';

	let things = $state([
		{ id: 1, fruit_name: 'apple' },
		{ id: 2, fruit_name: 'banana' },
		{ id: 3, fruit_name: 'carrot' },
		{ id: 4, fruit_name: 'doughnut' },
		{ id: 5, fruit_name: 'egg' }
	]);
	// const audio = new Audio();
	// audio.src = horn;
	// function honk() {
	// 	audio.load();
	// 	audio.play();
	// }

	import Canvas from './components/Canvas.svelte';

	const colors = ['red', 'orange', 'yellow', 'green', 'blue', 'indigo', 'violet', 'white', 'black'];

	let selected = $state(colors[0]);
	let size = $state(10);
	let showMenu = $state(true);
</script>

<Header
	logo="MyWebsite"
	links={[
		{ name: 'Home', href: '/' },
		{ name: 'Blog', href: '/blog' },
		{ name: 'Portfolio', href: '/portfolio' },
		{ name: 'Contact', href: '/contact' }
	]}
/>

<hr />
<h1>Looping in svelte</h1>

<EachLoops />

<hr />

<h1>Looping with id</h1>
{#each things as thing (thing.id)}
	<Thing name={thing.fruit_name} />
{/each}

<button onclick={() => things.shift()}> Remove first thing </button>
<hr />
<h2>Async MasterPiece</h2>
<AsyncMasterpiece />
<hr />
<h2>DOM Events</h2>
<DomEvents />
<hr />
<h2>Inline handler</h2>
<InlineHandler />

<hr />
<h2>passing functions as a props</h2>
<PassingFunctionToComp />
<!-- 
<h2>Spreading Props</h2>
<Spread onclick={honk} /> -->

<hr />
<h2>Text Input Binding</h2>
<TextInput />

<hr />
<h2>Number input Binding</h2>
<NumericInput />

<hr />
<h2>Check box Input Bindings</h2>
<CheckBoxInput />

<hr />
<h2>Select binding</h2>
<SelectBinding />

<hr />
<h2>Text Area Binding</h2>
<TextAreaBinding />

<hr />
<h2>Class Attributes</h2>
<p>
	class attributes are the attributes that we can use to modify the class as per the user events
</p>
<ClassAttributes />

<hr />
<h2>Style Attributes</h2>
<StyleAttribute />

<hr />
<h2>Components Styling</h2>
<ComponenetStyles />

<hr />
<h2>Canvas</h2>

<div class="container">
	<Canvas color={selected} {size} />

	{#if showMenu}
		<div
			role="presentation"
			class="modal-background"
			onclick={(event) => {
				if (event.target === event.currentTarget) {
					showMenu = false;
				}
			}}
			onkeydown={(e) => {
				if (e.key === 'Escape') {
					showMenu = false;
				}
			}}
		>
			<div class="menu">
				<div class="colors">
					{#each colors as color}
						<button
							class="color"
							aria-label={color}
							aria-current={selected === color}
							style="--color: {color}"
							onclick={() => {
								selected = color;
							}}
						></button>
					{/each}
				</div>

				<label>
					small
					<input type="range" bind:value={size} min="1" max="50" />
					large
				</label>
			</div>
		</div>
	{/if}

	<div class="controls">
		<button class="show-menu" onclick={() => (showMenu = !showMenu)}>
			{showMenu ? 'close' : 'menu'}
		</button>
	</div>
</div>

<style>
	.container {
		width: 100%;
		height: 1000px;
		position: relative;
	}

	.controls {
		position: absolute;
		left: 0;
		top: 0;
		padding: 1em;
	}

	.show-menu {
		width: 5em;
	}

	.modal-background {
		position: fixed;
		display: flex;
		justify-content: center;
		align-items: center;
		left: 0;
		top: 0;
		width: 100%;
		height: 100%;
		backdrop-filter: blur(20px);
	}

	.menu {
		position: relative;
		background: var(--bg-2);
		width: calc(100% - 2em);
		max-width: 28em;
		padding: 1em 1em 0.5em 1em;
		border-radius: 1em;
		box-sizing: border-box;
		user-select: none;
	}

	.colors {
		display: grid;
		align-items: center;
		grid-template-columns: repeat(9, 1fr);
		grid-gap: 0.5em;
	}

	.color {
		aspect-ratio: 1;
		border-radius: 50%;
		background: var(--color, #fff);
		transform: none;
		filter: drop-shadow(2px 2px 3px rgba(0, 0, 0, 0.2));
		transition: all 0.1s;
	}

	.color[aria-current='true'] {
		transform: translate(1px, 1px);
		filter: none;
		box-shadow: inset 3px 3px 4px rgba(0, 0, 0, 0.2);
	}

	.menu label {
		display: flex;
		width: 100%;
		margin: 1em 0 0 0;
	}

	.menu input {
		flex: 1;
	}
</style>
