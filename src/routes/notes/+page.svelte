<script lang="ts">
    import { supabase } from "$lib/supabaseClient";
    import { page } from "$app/stores";
    let bought = false;    

    async function downloadNotes() {
        if($page.data.session) {
            const { data, error } = await supabase.from('profiles').select('tokens').eq('id',$page.data.session.user.id)
            if(data[0].tokens < 97) {
                alert("Not enough tokens!");
                return;
            }
            const { error2 } = await supabase.from('profiles').update({ tokens: data[0].tokens - 97}).eq('id',$page.data.session.user.id)
            bought = true;
        }
    }
</script>

<div>
    <div class="card">
        <div class="title">
            <div style="font-weight: 700; font-size: 2em">Partial Derivatives</div>
            <div>Linear Algebra</div>
        </div>
        <div class="preview">
            <img src="https://lh3.googleusercontent.com/DAeLGsE71e2dNbcIr51s4ZGr-Z_CnrhW-wa50u8H2vO_jJ6zYovMU-RIR7bgKYz4Q3ru_L5qmp6rHfThDj9mktyZvGwTM6i3LA5dAg=w760-h360"/>
        </div>
        <div class="description">
            Notes for solving partial derivatives. Includes 5 mini lesson videos, 10 detailed exercises, and 10 worked out examples.
            <div class="align-right">
                <div style="flex-grow: 1"></div>
                <button on:click="{downloadNotes}" class="buy" disabled={bought}><span style="margin-right: 5px" class="material-symbols-outlined">generating_tokens</span>97: Buy Notes</button>
            </div>
        </div>
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
    .menu {
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .preview {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .card {
        display: flex;
        padding: 20px;
        box-sizing: border-box;
        flex-direction: column;
        justify-content: center;
        border-radius: 12px;
        border: 1px solid #49454F;
    }
    .preview {
        overflow: hidden;
    }
    .align-right {
        padding-top: 20px;
        display: flex;
    }
    .buy {
        display: flex;
        justify-content: center;
        align-items: center;
        color: #381E72;
        background-color: #C4AFF4;
        border: none;
        font-weight: 700;
        padding: 10px 20px 10px 20px;
        border-radius: 40px;
    }
    .buy:disabled {
        background-color: #5D5473;
    }
</style>
