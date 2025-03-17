<script>
const emojis = {
		apple: '🍎',
		banana: '🍌',
		carrot: '🥕',
		doughnut: '🍩',
		egg: '🥚'
	};

    let {name} = $props();
	// ...but `emoji` is fixed upon initialisation
	const emoji = emojis[name];
</script>


<p>{emoji} = {name}</p>