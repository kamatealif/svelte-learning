<script>
	import { onMount } from 'svelte';
	async function fetchData() {
		const res = await fetch('https://jsonplaceholder.typicode.com/posts/1');

		if (!res.ok) throw new Error('Failed to fetch data');
		return await res.json();
	}

	let dataPromise = $state('');
	onMount(() => {
		dataPromise = fetchData();
	});
</script>

{#await dataPromise}
	<p>Loading...</p>
{:then data}
	<p>Title: {data.title}</p>
	<p>Body: {data.body}</p>
{:catch error}
	<p>Error: {error.message}</p>
{/await}
