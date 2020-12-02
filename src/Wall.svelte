<script>

</script>

<div class='wall'>
	<slot></slot>
</div>

<style>

	.wall {
		background: rgb(204, 194, 165);
		height: 100%;
		width: 100%;
		margin: 0 auto;
		position: absolute;
		top: 0px;
		perspective-origin: center center;
		transform-style: preserve-3d;
	}
</style>