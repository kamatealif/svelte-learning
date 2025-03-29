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
