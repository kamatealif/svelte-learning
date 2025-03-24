<script>
	let isChecked = $state(false);
</script>

<form action="">
	<label>
		<input type="checkbox" bind:checked={isChecked} />
		yes Send me regular emails
	</label>
</form>

{#if isChecked}
	<p>Thank you. We will bombard your inbox and sell your personal details.</p>
{:else}
	<p>You must opt in to continue. If you're not paying, you're the product.</p>
{/if}

<button disabled={!isChecked}>Subscribe </button>

<style>
	button {
		background-color: #4caf50;
		border: none;
		color: white;
		padding: 15px 32px;
		text-align: center;
		text-decoration: none;
		display: inline-block;
		font-size: 16px;
		margin: 4px 2px;
		cursor: pointer;
	}
	button:disabled {
		opacity: 0.5;
	}
</style>
