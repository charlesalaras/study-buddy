<script>
    function downloadNotes(slug) {

    }
</script>

<div>
    <div class="card">
        <div class="title">
            <h1>Partial Derivatives</h1>
            <h2>Linear Algebra</h2>
        </div>
        <div class="preview">
            <img src="https://cdn.glitch.com/9c389208-b279-4e96-bcbc-e5f8712d8706%2Fplaceholder-landscape-short.png"/> 
        </div>
        <div class="description">

        </div>
    </div>
</div>

<style>
    .menu {
        display: flex;
        width: 100vw;
        align-items: center;
        justify-content: center;
    }
    .card {
        width: 90vw;
        border-radius: 12px;
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: 0.5fr 1.5fr 1fr;
        grid-column-gap: 0px;
        grid-row-gap: 0px;
    }
    .title { 
        width: 100%;
        grid-area: 1 / 1 / 2 / 2;
    }
    .preview { 
        width: 100%;
        height: 10vh;
        object-fit: fill;
        grid-area: 2 / 1 / 3 / 2; 
    }
    .description { 
        width: 100%;
        grid-area: 3 / 1 / 4 / 2; 
    } 
</style>
