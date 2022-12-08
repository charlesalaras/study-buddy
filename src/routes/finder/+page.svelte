<script lang="ts">
    import { supabase } from "$lib/supabaseClient";
    let active: boolean = true;
    let buddies = [];

    let school: string | null = null;
    let major: string | null = null;
    let classes: string | null = null;

    async function runQuery() {
        if(!school && !major && !classes) {
            alert("Please enter a query!");
            return;
        }
        
        const query = {
            ...(school ? {school} : {}),
            ...(major ? {major} : {}),
        };
        try {
            let { data, error } = await supabase.from('profiles').select()
                .match(query)
                .contains('courses', [classes]);
            console.log(data);
            buddies = data;
        if (error) throw error
        } catch (error) {
            if (error instanceof Error) {
                alert(error.message)
            }
        } finally {
            console.log("end of function!");
            active = false;
            console.log(active);
        }
    }
</script>

<div>
    {#if active}
    <form on:submit|preventDefault="{runQuery}">
        <div class="form-block">
        <label for="school">University</label>
        <input class="field" type="text" placeholder="University" id="school" bind:value="{school}"/>
        </div>
        <div class="form-block">
        <label for="school">Major</label>
        <input class="field" type="text" placeholder="Major" id="major" bind:value="{major}"/>
        </div>
        <div class="form-block">
        <label for="school">Courses</label>
        <input class="field" type="text" placeholder="Courses" id="courses" bind:value="{classes}"/>
        </div>
        <div class="form-submit">
            <button class="submit"><span class="material-symbols-outlined">search</span>FIND MY STUDY BUDDY</button>
        </div>
    </form>
    {:else}
        <button class="return" on:click="{() => {active = !active}}">
            <span class="material-symbols-outlined">arrow_back_ios</span>Return
        </button>
        {#each buddies as buddy}
            <div class="card">
                <div class="profile-pic">

                </div>
                <div class="card-details">
                    <div style="font-size: 1.5em; font-weight: 700">{buddy.username}</div>
                    <div>{buddy.school}</div>
                    <div>{buddy.major}</div>
                    <button class="return">
                        <span style="margin-right: 5px" class="material-symbols-outlined">person_add</span> Study with Buddy
                    </button>
                </div>
            </div>
        {/each}
    {/if}
</div>

<style>
    .material-symbols-outlined {
        font-variation-settings:
        'FILL' 0,
        'wght' 700,
        'GRAD' 0,
        'opsz' 40
    }
    .return {
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
    .card {
        padding: 10px;
        margin-top: 10px;
        margin-bottom: 10px;
        width: 100%;
        display: flex;
        flex-direction: row;
        align-items: center;
        border: 2px solid #49454F;
        border-radius: 12px;
    }
    .card-details {
        display: flex;
        flex-direction: column;
        justify-content: center;
        gap: 5px;
    }
    .form-submit {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .submit {
        display: flex;
        justify-content: center;
        align-items: center;
        color: #381E72;
        background-color: #C4AFF4;
        border: none;
        font-weight: 700;
        width: 100%;
        padding-top: 20px;
        padding-bottom: 20px;
        border-radius: 40px;
    }
    .form-block {
        padding-top: 10px;
        padding-bottom: 10px;
    }
    .field {
        width: 100%;
        height: 3em;
        padding: 10px 10px 10px 20px;
        background-color: #49454F;
        color: #E6E1E5;
        border-radius: 4px 4px 0px 0px;
        border-width: 0px 0px 1px 0px;
        border-style: none none solid none;
        border-color: #E6E1E5;
        box-sizing: border-box;
    }
    .field:focus {
        outline: none !important;
        border-width: 0px 0px 3px 0px;
        border-color: #D0BCFF;
    }
</style>
