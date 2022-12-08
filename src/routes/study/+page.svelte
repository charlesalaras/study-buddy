<script>
    import { tweened } from "svelte/motion";
    let main = 25 * 60;
    let rest = 5 * 60;
    let loops = 4;
    let timer = tweened(main);

    setInterval(() => {
        if($timer > 0) $timer--;
    }, 1000);

    $: minutes = Math.floor($timer / 60);
    $: seconds = Math.floor($timer - minutes * 60);
</script>

<div><span>Loop </span><span>{loops - 4}</span></div>
<div class="timer">
        <span>{minutes}</span>:<span>{seconds === 0 ? "00" : seconds}</span>
</div>

<style>
    .timer {
        position: absolute;
        left: 0px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 4em;
        font-weight: 700;
        width: 100vw;
    }
</style>
