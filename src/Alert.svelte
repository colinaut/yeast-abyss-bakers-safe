<script>
    import { fade } from 'svelte/transition';
    import { onMount } from 'svelte';

    export let text = false
    const textBasedDuration = text.length * 80
    export let duration = (textBasedDuration > 4000) ? textBasedDuration : 4000;
    export let color

    const delay = m => new Promise(r => setTimeout(r, m))

    onMount( async () => {
        await delay(duration)
        text = ''
    })

</script>

{#if text}
    <div class={`backdrop ${color}`} transition:fade on:click={() => text = false}>
        <div class="alert">
            {text}
        </div>
    </div>
{/if}


<style>
    .backdrop {
        position: absolute;
        top: 0px;
        left: 0px;
        width: 100%;
        height: 100%;
        z-index: 100;
        background: rgba(0, 0, 0, 0.6);
    }
    .alert {
        border-radius: 15px;
        margin: 5px auto;
        width: 30vw;
        padding: 1em;
        position: absolute;
        font-size: 1.6em;
        top: 50%;
		left: 50%;
        text-align: center;
        font-weight: 700;
		transform: translateY(-50%) translateX(-50%);
        color: #000;
        background: #fff;
        border: 2px solid #000;
        box-shadow: 5px 5px 15px rgba(0, 0, 0, 0.6);
        line-height: 130%;
    }
    .red .alert {
        color: #fff;
        background:rgba(182, 5, 5, 0.8);
        border: 2px solid #fff;
    }
    .green .alert {
        color: #fff;
        background:rgba(5, 182, 14, 0.8);
        border: 2px solid #fff;
    }
</style>