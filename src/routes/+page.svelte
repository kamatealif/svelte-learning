<script lang="ts">
	import Header from './Header.svelte';

	let formState = $state({
		name: '',
		birthday: '',
		step: 0,
		error: ''
	});
</script>

<Header/>
<main>
	<p>Step : {formState.step}</p>

	{#if formState.error}
		<p class="error">{formState.error}</p>
	{/if}

	{#if formState.step == 0}
		<div>
			<label for="name">Your Name</label>
			<input type="text" id="name" bind:value={formState.name} />
		</div>
		<button
			onclick={() => {
				if (formState.name !== '') {
					formState.step = formState.step + 1;
				} else {
					formState.error = 'Your name is Empty. Please write Your name.';
				}
			}}>Next</button
		>
	{:else if formState.step == 1}
		<div>
			<label for="bday">Your BirthDay</label>
			<input type="date" id="bday" bind:value={formState.birthday} />
		</div>
		<button
			onclick={() => {
				if (formState.birthday !== '') {
					formState.step = formState.step + 1;
                    formState.error = '';
				} else {
					formState.error = 'Your BirthDay is Empty. Please write Your BirthDay.';
				}
			}}>Next</button
		>
	{/if}
</main>

<style>
	.error {
		background-color: tomato;
        color:white;
        border-radius: 4px;
        padding: 10px;
        font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
	}
</style>
