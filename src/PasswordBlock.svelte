
<script>
	export let text
	export let show = false
</script>

<div class:show>
	{text}
</div>


<style>
	div {
		width: 1.4em;
		height: 2em;
		border: 1px solid #333;
		border-radius: 2px;
		text-align: center;
		line-height: 2em;
		background: #ccc;
		text-indent: -10000px;
		text-transform: uppercase;
	}
	
	.show {
		background: #ee6;
		text-indent: 0px;
	}
	
	.spacer {
		background: #000;
	}
</style>