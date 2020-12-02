<script>
	import PasswordBlock from './PasswordBlock.svelte'
	export let passwordBlocks
</script>

<div>
	{#each passwordBlocks as block}
	<PasswordBlock text={block.letter} show={block.guessed} />
	{/each}
</div>

<style>
	div {
		display: flex;
		justify-content: space-between;
		margin: 20px 20px;
		padding: 0;
	}
</style>