<script>
    import { onMount } from 'svelte';
    import CoinCard from "./lib/CoinCard.svelte";
    import Loader from './lib/Loader.svelte';
    import UpdateButton from './lib/UpdateButton.svelte';

    let name = "Crypto Tracker";

    let coins = [];

    async function fetchCoins() {
        const response = await fetch(
            "https://api.coinstats.app/public/v1/coins?limit=20"
        );
        const data = await response.json();
        coins = data.coins;
        console.log(coins);
    }

    onMount(fetchCoins)
</script>

<main>
    <h1>{name}</h1>

    {#if coins.length === 0}
        <Loader/>
    {:else}
        <UpdateButton {fetchCoins}/>
        <div class="grid">
            {#each coins as coin}
                <CoinCard {coin} />
            {/each}
        </div>
    {/if}

    <p>
        Visit <a href="https://svelte.dev">svelte.dev</a> to learn how to build Svelte
        apps.
    </p>
    <p>new_by_4_at_1578906096</p>
</main>

<style>
    :root {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
            Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    }

    main {
        text-align: center;
        padding: 1em;
        margin: 0 auto;
    }

    main {
        text-align: center;
        padding: 40px 0;
        margin: 0 auto;
    }
    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }
    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
        gap: 30px;
    }
    @media (min-width: 640px) {
        main {
            max-width: 1600px;
            padding: 40px 20px;
        }
    }
</style>
