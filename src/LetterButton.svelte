<script>
import { createEventDispatcher } from 'svelte';
const dispatch = createEventDispatcher();
export let text;
export let pressed = false;
export let correct = false;
function click() {
	dispatch('message', {
		text: text,
		correct: correct,
		pressed: pressed
	});
}

</script>

<button on:click={click} class:pressed class:correct class:space={(text === ' ')} >
	{(text !== ' ') ? text : 'space'}
</button>


<style>
	button {
		background: #eee;
		border-radius: 50%;
		width: 2em;
		height: 2em;
		font-size: .8em;
		line-height: 1em;
		border: 1px solid #333;
		margin: .2em;
		background: #444;
		color: #fff;
		text-transform: uppercase;
		cursor: pointer;
	}
	.space {
		width: 5em;
		height: 2.3em;
		border-radius: 2em;
		font-size: .7em;
	}
	.pressed {
		background: #943;
	}
	.pressed.correct {
		background: #990;
	}
</style>