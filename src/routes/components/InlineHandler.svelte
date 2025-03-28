<script>
	let m = $state({ x: 0, y: 0 });

	function onpointermove(event) {
		m.x = event.clientX;
		m.y = event.clientY;
	}
</script>

<div {onpointermove}>
	The pointer is at {Math.round(m.x)} x {Math.round(m.y)}
</div>

<style>
	div {
		width: 100%;
		height: 100px;
		padding: 1rem;
		background-color: rgba(255, 0, 0, 0.5);
		border: solid red 2px;
		border-radius: 10px;
	}
</style>
