<script>
    import { createEventDispatcher } from 'svelte';
    import { fade } from 'svelte/transition';
    const dispatch = createEventDispatcher();
    function click() {
        dispatch('message', {
            clicked: true
        });
    }
</script>

<div transition:fade="{{ duration: 1000 }}" on:click={click}>
    <img src="./images/painting.jpg" alt="painting of Palarmi as king" />
</div>


<style>
    div {
        width: 21em;
        height: 34vh;
        position: absolute;
        z-index: 2;
        margin: 0 auto;
        top: 48%;
        left: 50%;
        transform: translateY(-50%) translateX(-50%);
        background-color: #000;
        cursor: pointer;
        box-shadow: 0 0 0 1px rgb(71, 71, 67),
            0 0 0 12px rgb(0, 0, 0),
            0 0 0 13px rgb(218, 189, 63),
            0 0 0 16px rgb(71, 52, 11),
            0 0 0 34px rgb(218, 189, 63),
            0 0 0 36px rgb(48, 41, 1),
            5px 5px 10px 36px rgb(48, 41, 1);
    }

    img {
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: 20% 0%;
    }

</style>