<script lang="ts">
    import Header from './Header.svelte';
    import Footer from './Footer.svelte';
    import './styles.css';
    import { supabase } from "$lib/supabaseClient"
    import { invalidate } from "$app/navigation"
    import { onMount } from "svelte"
    import { page } from "$app/stores"

    onMount(() => {
        const { data: { subscription }, } = supabase.auth.onAuthStateChange(() => { invalidate('supabase:auth') })
        
        return () => { subscription.unsubscribe() }
    })

</script>
<svelte:head>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200" />
    <link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com" crossorigin><link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">
</svelte:head>

<div class="app">
	<Header avatarUrl={$page.data.session ? $page.data.session.user.avatarUrl : undefined}/>

	<main>
		<slot />
	</main>

    <Footer/>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
        min-height: 100vh;
        color: #E6E1E5;
        background-color: #1C1B1F;
        font-family: "Roboto";
	}

	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>
