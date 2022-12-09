<script>
    import { tweened } from "svelte/motion";
    let main = 30 * 60;
    let rest = 5 * 60;
    let loops = 0;
    let timer = tweened(main);
    let pauseTime = false;
    let stop = false;

    setInterval(() => {
        if(!stop) {
        if($timer > 0) $timer--;
        if($timer <= rest) {
            pauseTime = true;
        }
        if(loops == 4) {
            stop = true;
        }
        if($timer <= 0) {
            $timer = 30 * 60;
            pauseTime = false;
            loops++;
        }
        }
    }, 1000);

    $: minutes = Math.floor($timer / 60);
    $: seconds = Math.floor($timer - minutes * 60);
</script>
<div class="test">
    <div>{loops} / 4</div>
    <div class="timer" style="background-color: {pauseTime ? "#F2B8B5" : "#601410"}">
        <span>{minutes}</span>:<span>{seconds < 10 ? "0" + seconds : seconds}</span>
    </div>
    {#if pauseTime}
        <div style="font-weight: 700">Break Time!</div>
    {:else}
        <div style="font-weight: 700">Pomodoro Time!</div>
    {/if}
</div>

<style>
    .test {
        display: flex;
        align-items: center;
        justify-content: center;
        flex-direction: column;
        gap: 20px;
    }
    .timer {
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 4em;
        font-weight: 700;
        width: 30vh;
        height: 30vh;
        border-radius: 15vh;
    }
</style>
