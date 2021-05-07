<script>
    // Range
    import {range} from '../range'

    var cityCards = [
        {
            name: "Delhi"
        },
        {
            name: "Kanpur"
        }
    ]
    
    import {blogCards} from "../blogCards"
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

<section>
    <div class="width-restriction">
        <section class="choose-city-section">
            <h1>Select your city</h1>
            <br/>
            <div class="row">
                {#each range(0,4,1) as i, index}
                {#each cityCards as city, j}
                    {#if j%3 == i}
                    <div class="col-4">
                        <a href="/city/{city.name}">
                            <div class="card" style="text-align: center">
                                <div class="width-restriction">
                                    <h2>{city.name}</h2>
                                </div>
                            </div>
                        </a>
                    </div>
                    {/if}
                {/each}
                {/each}

            </div>
        </section>

        <br/><br/>
    
        <!-- <section class="blog-section">
            <h1>Quick resources and Blog</h1>
            <br/>
            <div class="row">
                {#each range(0,3,1) as i, index}
                {#each blogCards as blog, j}
                    {#if j%3 == i}
                    <div class="col-3">
                        <a href="/blog/{blog.id}">
                            <div class="card">
                                <div class="width-restriction">
                                    <h2>{blog.title}</h2>
                                    <p>{blog.subtext}</p>
                                </div>
                            </div>
                        </a>
                    </div>
                    {/if}
                {/each}
                {/each}
            </div>
        </section>

        <br/><br/> -->

        <section class="donate-section">
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
                                <a href="{donation.link}" style="color: var(--link-green); font-weight: bold" target="__blank">Donate</a>
                            </div>
                        </div>
                    </div>
                    {/if}
                {/each}
                {/each}
            </div>
        </section>
    </div>
</section>