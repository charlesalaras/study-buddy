<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
    import welcome_fallback from '$lib/images/svelte-welcome.png';

    import { page } from "$app/stores"
    import Account from "./Account.svelte"
    import Auth from "./Auth.svelte"
</script>

<svelte:head>
	<title>Supabase + SvelteKit</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
    {#if !$page.data.session}
    <Auth/>
    {:else}
        <Account session ="{$page.data.session}" />
    {/if}
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
