<script>
    export let coin;

    /**
     * @param {number} priceChange
     */
    function changeIsPositive(priceChange) {
        return priceChange >= 0;
    }
</script>

<div class="coin-card">
    <img class="coin-image" src={coin.icon} alt={coin.name} />
    <p class="coin-name">{coin.name}</p>
    <div class="coin-details">
        <div
            class="detail-field price-change"
            class:positive={changeIsPositive(coin.priceChange1w)}
        >
            {coin.priceChange1w}%
        </div>
        <div class="detail-field">{coin.price.toFixed(2)}$</div>
        {#if coin.websiteUrl}
            <a class="detail-field" href={coin.websiteUrl}>Site &#8594;</a> 
        {:else}
            <span class="detail-field">No Site</span>
        {/if}
    </div>
</div>

<style>
    .coin-card {
        display: block;
        top: 0px;
        position: relative;
        background-color: #f2f8f9;
        border-radius: 4px;
        margin: 12px;
        text-decoration: none;
        z-index: 0;
        overflow: hidden;
        border: 1px solid #f2f8f9;
        transition: all 0.2s ease-out;
    }
    .coin-card:hover {
        transition: all 0.2s ease-out;
        box-shadow: 0px 4px 8px rgba(38, 38, 38, 0.2);
        top: -4px;
        border: 1px solid #cccccc;
        background-color: white;
    }
    .coin-image {
        max-width: 4rem;
        margin-top: 10px;
    }
    .coin-name {
        font-size: 24px;
        font-weight: bold;
        margin-top: 15px;
    }
    .coin-details {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        border-top: 1px solid #d1d5db;
        background-color: #f3f4f6;
    }
    .detail-field {
        font-size: 15px;
        font-weight: bold;
        padding: 15px 0;
    }
    a.detail-field {
        text-decoration: none;
        color: blue;
    }
    a.detail-field:hover {
        color: cornflowerblue;
    }
    .detail-field:not(:last-child) {
        border-right: 1px solid #d1d5db;
    }
    .price-change {
        color: #dc2626;
    }
    .positive {
        color: #16a34a;
    }
    @media (min-width: 1024px) {
        .detail-field {
            font-size: 18px;
            padding: 15px;
        }
    }
</style>
