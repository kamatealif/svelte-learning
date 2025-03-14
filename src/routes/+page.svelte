<script lang="ts">
	import Header from './Header.svelte';

	let formState = $state({
		name: '',
		birthday: '',
		step: 0,
		error: ''
	});
</script>

<Header 
  logo="MyWebsite"
  links={[
    { name: "Home", href: "/" },
    { name: "Blog", href: "/blog" },
    { name: "Portfolio", href: "/portfolio" },
    { name: "Contact", href: "/contact" }
  ]}
/>
<main class="form-container">
    <p class="step-indicator">Step: {formState.step + 1}</p>

    {#if formState.error}
        <p class="error-message">{formState.error}</p>
    {/if}

    {#if formState.step == 0}
        <div class="form-group">
            <label for="name">Your Name</label>
            <input
                type="text"
                id="name"
                bind:value={formState.name}
                placeholder="Enter your name"
            />
        </div>
        <button
            class="btn"
            onclick={() => {
                if (formState.name.trim() !== '') {
                    formState.step += 1;
                    formState.error = '';
                } else {
                    formState.error = 'Your name is empty. Please enter your name.';
                }
            }}
        >
            Next
        </button>

    {:else if formState.step == 1}
        <div class="form-group">
            <label for="bday">Your Birthday</label>
            <input
                type="date"
                id="bday"
                bind:value={formState.birthday}
            />
        </div>
        <button
            class="btn"
            onclick={() => {
                if (formState.birthday.trim() !== '') {
                    formState.step += 1;
                    formState.error = '';
                } else {
                    formState.error = 'Your birthday is empty. Please enter your birthday.';
                }
            }}
        >
            Next
        </button>
    {/if}
</main>

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
        color: #4CAF50;
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
        width: 100%;
        padding-left: 0.5rem;
        padding-block:1rem;
        border: 2px solid #ddd;
        border-radius: 8px;
        outline: none;
        transition: border 0.3s;
    }

    .form-group input:focus {
        border-color: #4CAF50;
        box-shadow: 0 0 6px rgba(76, 175, 80, 0.3);
    }

    .btn {
        background-color: #4CAF50;
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