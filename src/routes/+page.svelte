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

<style>
	.form-container {
		max-width: 400px;
		margin: 2rem auto;
		padding: 2rem;
		background-color: #f9f9f9;
		border: 2px solid #ddd;
		border-radius: 12px;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
		text-align: center;
		font-family: 'Arial', sans-serif;
	}

	.step-indicator {
		font-size: 1.2rem;
		margin-bottom: 1rem;
		color: #4caf50;
		font-weight: bold;
	}

	.error-message {
		width: auto;
		font-size: small;
		color: #e74c3c;
		background-color: #fee;
		border: 1px solid #e74c3c;
		padding: 1rem;
		border-radius: 6px;
		margin-bottom: 1rem;
	}

	.form-group {
		margin-bottom: 1.5rem;
		text-align: left;
	}

	.form-group label {
		display: block;
		margin-bottom: 0.5rem;
		font-weight: bold;
		color: #333;
	}

	.form-group input {
		width: 95%;
		padding-block: 1rem;
		border: 2px solid #ddd;
		border-radius: 8px;
		outline: none;
		transition: border 0.3s;
		padding-inline: 0.5rem;
	}

	.form-group input:focus {
		border-color: #4caf50;
		box-shadow: 0 0 6px rgba(76, 175, 80, 0.3);
	}

	.btn {
		background-color: #4caf50;
		color: #fff;
		border: none;
		padding: 0.8rem 2rem;
		border-radius: 8px;
		cursor: pointer;
		transition: background-color 0.3s;
	}

	.btn:hover {
		background-color: #45a049;
	}

	.btn:focus {
		outline: none;
		box-shadow: 0 0 8px rgba(76, 175, 80, 0.5);
	}
</style>
