<script>
    import CoinCard from "./lib/CoinCard.svelte";

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
</script>

<main>
    <h1>{name}</h1>

    {#if coins.length === 0}
        <button on:click={fetchCoins} class="myButton">Fetch Coin Data!</button>
    {:else}
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
    <p>
        new_by_4_at_1578906096
    </p>
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

    .myButton {
        box-shadow: inset 0px 1px 0px 0px #ffffff;
        background: linear-gradient(to bottom, #ffffff 5%, #f6f6f6 100%);
        background-color: #ffffff;
        border-radius: 6px;
        border: 1px solid #dcdcdc;
        display: inline-block;
        cursor: pointer;
        color: #666666;
        font-family: Arial;
        font-size: 15px;
        font-weight: bold;
        padding: 6px 24px;
        text-decoration: none;
        text-shadow: 0px 1px 0px #ffffff;
    }
    .myButton:hover {
        background: linear-gradient(to bottom, #f6f6f6 5%, #ffffff 100%);
        background-color: #f6f6f6;
    }
    .myButton:active {
        position: relative;
        top: 1px;
    }
</style>
