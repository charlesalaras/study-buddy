<script>

</script>

<div>
    <form>
        <div class="form-block">
        <label for="school">University</label>
        <input class="field" type="text" placeholder="University" id="school"/>
        </div>
        <div class="form-block">
        <label for="school">Major</label>
        <input class="field" type="text" placeholder="Major" id="major"/>
        </div>
        <div class="form-block">
        <label for="school">Courses</label>
        <input class="field" type="text" placeholder="Courses" id="courses"/>
        </div>
        <div class="form-submit">
            <button class="submit"><span class="material-symbols-outlined">search</span>FIND MY STUDY BUDDY</button>
        </div>
    </form>
</div>

<style>
    .material-symbols-outlined {
        font-variation-settings:
        'FILL' 0,
        'wght' 700,
        'GRAD' 0,
        'opsz' 40
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
