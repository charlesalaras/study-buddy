<script>
    function downloadNotes(slug) {

    }
</script>

<div class="menu">
    <div class="card">

    </card>
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
        border-radius: 14px;
        display: grid;
        grid-template-columns: 1fr;
        grid-template-rows: 0.5fr 1.5fr 1fr;
        grid-column-gap: 0px;
        grid-row-gap: 0px;
    }
    .title { grid-area: 1 / 1 / 2 / 2; }
    .preview { grid-area: 2 / 1 / 3 / 2; }
    .description { grid-area: 3 / 1 / 4 / 2; } 
</style>
