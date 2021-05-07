<script>
    // Range
    import {range} from '../range'

    import {blogCards} from "../blogCards"
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
        <h1>Quick resources and Blog</h1>
        <br/>
        <p>🛠 We're still working on this content</p>
        <!-- <div class="row">
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
        </div> -->
    </div>
</section>