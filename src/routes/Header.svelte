<script lang="ts">
    import { supabase } from '$lib/supabaseClient'
    export let avatarUrl;
    export let tokens;

  let absoluteURL: string | null = null
  const downloadImage = async (path: string) => {
    try {
      const { data, error } = await supabase.storage.from('avatars').download(path)

      if (error) {
        throw error
      }

      const url = URL.createObjectURL(data)
      absoluteURL = url
    } catch (error) {
      if (error instanceof Error) {
        console.log('Error downloading image: ', error.message)
      }
    }
  }

$: if(avatarUrl) {
    console.log(avatarUrl)
    downloadImage(avatarUrl)
}
</script>

<header>
    <div class="tokens">
        <span class="material-symbols-outlined">generating_tokens</span>
        {#if tokens !== undefined}
            {tokens}
        {/if}
    </div>
    <div>
        <a class="title" href="/">Study Buddy</a>
    </div>
    {#if avatarUrl}
        <img class="profile-pic" src="{absoluteURL}" alt={avatarUrl ? "Profile Picture" : "No image"}/>
    {:else}
        <div class="profile-pic"></div>
    {/if}
</header>

<style>
    .material-symbols-outlined {
      font-variation-settings:
      'FILL' 0,
      'wght' 400,
      'GRAD' 0,
      'opsz' 48
    }
    header {
        color: #E6E1E5;
        background-color: #1C1B1F;
        font-size: 2em;
        height: 10vh;
		display: flex;
        justify-content: space-evenly;
        align-items: center;
        width: 100vw;
    }
    .title {
        font-weight: 700;
        color: #E6E1E5;
        text-decoration: none;
    }
    .title:hover {
        color: #D0BCFF;
    }
    .tokens {
        width: 10vh;
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        align-items: center;
        font-size: 0.75em;
    }
    .profile-pic {
        height: 50%;
        border-radius: 50%;
        aspect-ratio: 1 / 1;
    }
	nav {
		display: flex;
		justify-content: center;
		--background: rgba(255, 255, 255, 0.7);
	}

	svg {
		width: 2em;
		height: 3em;
		display: block;
	}

	path {
		fill: var(--background);
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	li[aria-current='page']::before {
		--size: 6px;
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		top: 0;
		left: calc(50% - var(--size));
		border: var(--size) solid transparent;
		border-top: var(--size) solid var(--color-theme-1);
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color: var(--color-text);
		font-weight: 700;
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--color-theme-1);
	}
</style>
