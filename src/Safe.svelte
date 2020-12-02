<script>
export let open = false
</script>
<div class='wrapper'>
	<div class='safe' class:open>
		<slot></slot>
	</div>
</div>

<style>
	.wrapper {
		background-color: rgb(41, 44, 51);
		background-image: url('/images/books.png');
		background-position: 80% 80%;
		background-repeat: no-repeat;
		background-size: 40%;
		border: 2px solid #000;
		width: 23em;
		height: 15em;
		margin: 0 auto;
		border-radius: 6px;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translateY(-50%) translateX(-50%);
		perspective: 200vh;
	}
	.safe {
		background: #888;
		border: 2px solid #333;
		width: 100%;
		height: 100%;
		margin: 0 auto;
		border-radius: 6px;
		transition: transform 3s;
		transform-style: preserve-3d;
		transform: translateZ(5em);
	}
	.open {
		transform: rotateY(-60deg) translateZ(10em) translateX(6em);
	}
</style>
