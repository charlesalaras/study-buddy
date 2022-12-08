<script>
    import { page } from "$app/stores";
    import { goto } from "$app/navigation";
</script>

<div class="footer">
    <div class="nav-button">
        <button class:selected="{$page.url.pathname === '/finder'}"
            class="icon"
            on:click={() => {goto('/finder')}}><span class="material-symbols-outlined">face</span></button>
        <div>Finder</div>
    </div>
    <div class="nav-button">
        <button class:selected="{$page.url.pathname === '/study'}" 
            class="icon" 
            on:click={() => {goto('/study')}}><span class="material-symbols-outlined">timer</span></button>
        <div>Study</div>
    </div>
    <div class="nav-button">
        <button class:selected="{$page.url.pathname === '/notes'}"
            class="icon" 
            on:click={() => {goto('/notes')}}><span class="material-symbols-outlined">edit_note</span></button>
        <div>Notes</div>
    </div>
</div>

<style>

    .material-symbols-outlined {
      font-variation-settings:
      'FILL' 0,
      'wght' 400,
      'GRAD' 0,
      'opsz' 48
    }
    .icon {
        color: #E8DEF8;
        border: none;
        background-color: transparent;
        border-radius: 2vh;
        width: 10vh;
        padding: 0.5vh;
    }
    .selected{
        background-color: #4A4458;
    }
    .nav-button {
        height: 10vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: space-evenly;
        font-weight: 700;
    }
    .footer {
        color: #CAC4D0;
        background-color: #2B2831;
        display: flex;
        align-items: center;
        justify-content: space-evenly;
        width: 100vw;
        height: 10vh;
    }
</style>
