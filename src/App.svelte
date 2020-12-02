<script>
	import LetterButton from './LetterButton.svelte'
	import Wall from './Wall.svelte'
	import Floor from './Floor.svelte'
	import Alert from './Alert.svelte'
	import Safe from './Safe.svelte'
	import Painting from './Painting.svelte'
	import PasswordBlocks from './PasswordBlocks.svelte'
	import Keyboard from './Keyboard.svelte'

	const password = 'poetking!123'
	const letters = '1234567890abcdefghijklmnopqrstuvwxyz.!?'
	let safeHidden = true
	let safeOpen = false
	let wrongAnswers = 0
	let alertText = false
	let alertColor

	let passwordBlocks = [...password].map(x => {
		return {letter: x, guessed: false }
	})

	let letterButtons = [...letters].map(x => {
		return {letter: x, pressed: false, correct: false }
	})

	const buttonClick = (event) => {
		if (!event.detail.pressed && !safeOpen) { // Only activate if it has yet to be pressed and not open
			const letter = event.detail.text
			const isPasswordChar = passwordBlocks.some(block => block.letter === letter)

			// Set state of letterButtons
			letterButtons = letterButtons.map( letterButton => {
				if (letterButton.letter === letter) return { ...letterButton, pressed: true, correct: isPasswordChar}
				return letterButton
			})

			// if user selects right answer set state of passwordBlocks
			if (isPasswordChar) {
				passwordBlocks = passwordBlocks.map( block => {
					if (block.letter === letter) return { ...block, guessed: true }
					return block
				})
			} else {
				wrongAnswers += 1; // else increment state of wrongAnswers

				// Trigger alert
				switch (wrongAnswers) {
					case 1: alertText = 'BUZZ! Wrong key! The floor slides open a crack revealing a dark and sweet smelling pit!'; alertColor = 'red'; break;
					case 2: alertText = 'BUZZ!! The floor slides further! Something gooey moves in the darkness below!'; break;
					case 3: alertText = 'BUZZ!!! The gap widens becoming impossible to jump!'; break;
					case 4: alertText = 'BUZZ!!!! Only a small ledge remains! (Roll DEX to avoid falling!)'; break;
					case 5: alertText = 'BUZZ!!!!! The floor is gone!'; break;
				}
			}

			// If all characters guessed then set safeOpen to true
			if (!passwordBlocks.some(block => block.guessed === false)) {
				safeOpen = true
				alertText = 'You cracked the password! The safe opens!';
				alertColor = 'green';
			}
		}
	}

	const paintingClick = () => {
		safeHidden = false;
		alertText = 'You remove the painting and find a large password locked safe!';
	}
</script>

<div class='wrapper'>
	<div class="room">
		<Wall>
			{#if safeHidden}
				<Painting on:message={paintingClick} />
			{:else}
				<Safe open={safeOpen}>
					<PasswordBlocks passwordBlocks={passwordBlocks} />
					<Keyboard>
						{#each letterButtons as button}
							<LetterButton on:message={buttonClick} text={button.letter} pressed={button.pressed} correct={button.correct}/>
						{/each}
					</Keyboard>
				</Safe>
				{#if alertText}
					<Alert bind:text={alertText} color={alertColor} />
				{/if}
			{/if}
		</Wall>
		<Floor wrongAnswers={wrongAnswers} open={safeOpen} />
	</div>
</div>


<style>
	.wrapper {
		width: 100vw;
		height: 100vh;
		overflow: hidden;
	}
	.room {
		margin: 0 auto;
		height: 50vh;
		width: 60vw;
		perspective: 100vh;
		perspective-origin: center center;
		transform-style: preserve-3d;
		position: relative;
	}
	:global(body) {
		background: rgb(146, 137, 105);
		padding: 0;
	}

</style>