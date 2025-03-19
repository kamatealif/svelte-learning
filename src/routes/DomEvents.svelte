<script>
	let m = $state({ x: 0, y: 0 });

	function onpointermove(event) {
		m.x = event.clientX;
		m.y = event.clientY;
	}
</script>

<div class="container" {onpointermove}>
	<p>Mouse position: x:{Math.ceil(m.x)}, y:{Math.ceil(m.y)}</p>
</div>

<style>
	.container {
		background-color: rgba(0, 255, 0, 0.5);
		height: 500px;
		width: 500px;
		margin: 0 auto;
		padding: 10px 10px;
	}
</style>
