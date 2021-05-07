<script>
    // Range
    import {range} from '../range'

    import {donations} from "../donate"
</script>

<style>
    .card h3 {
        margin-bottom: 5px;
        transition: 0.2s;
    }
    .card:hover h3, .card:hover h2 {
        color: var(--link-green)
    }
</style>

<section class="blog-section">
    <div class="width-restriction">
        <h1>Donate</h1>
        <br/>
        <div class="row">
            {#each range(0,3,1) as i, index}
            {#each donations as donation, j}
                {#if j%3 == i}
                <div class="col-3">
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{donation.org}</h2>
                            <p>{donation.description}</p>
                            <a href="{donation.link}" target="_blank" style="color: var(--link-green); font-weight: bold">Donate</a>
                        </div>
                    </div>
                </div>
                {/if}
            {/each}
            {/each}
        </div>
    </div>
</section>