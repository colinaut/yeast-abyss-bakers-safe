<script>
	export let wrongAnswers
	export let open = false

</script>


<div class='pit'>
	<div class={`floor level${wrongAnswers}`} class:open>
	</div>
</div>


<style>
	.pit {
		background-color: #000;
		background-image: url('/images/breadpudding.jpg');
		background-size: 40%;
		background-position: center 70%;
		background-repeat: no-repeat;
		height: 100vh;
		width: 100%;
		margin: 0 auto;
		transform: rotateX(90deg) translateY(50vh);
		position: absolute;
		top: 0px;
	}
	.floor {
		background: rgb(136, 115, 71);
		height: 0%;
		width: 100%;
		position: absolute;
		top: 0px;
		transition: all 2s;
		border-bottom: 40px solid rgb(53, 44, 35);
	}
	.floor.level0, .floor.open {
		height: 100% !important;
	}
	.floor.level1 {
		height: 60%;
	}
	.floor.level2 {
		height: 40%;
	}
	.floor.level3 {
		height: 20%;
	}
	.floor.level4{
		height: 10%;
	}
</style>