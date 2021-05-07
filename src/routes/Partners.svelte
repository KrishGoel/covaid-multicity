<script>
    // Range
    // import { donations } from '../donate'
    import {range} from '../range'

    const partners = [
        {
            org: "Students for India",
            description: "StudentsforIndia is a not-for-profit student organisation that has already provided masks and vital daily supplies to over 50,000 families. An ever growing team of hundreds of students from across India stretching from the Northeast to Delhi to the South, we've made it our mission to work on creating a more equitable and supportive society. In the second wave of the pandemic we’ve been working to provide sanitary pads to girls in rural schools and essential supplies to those in rural areas while working as one with CoVAID to verify and get leads to those in need.",
            link: ""
        }
    ]
</script>

<style>
    .card h3 {
        margin-bottom: 5px;
    }
</style>

<section class="partners-section">
    <div class="width-restriction">
        <h1>Partner Organisations</h1>
        <br/>
        <div class="row">
            {#each range(0,3,1) as i, index}
            {#each partners as partner, j}
                {#if j%3 == i}
                <div class="col-3">
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{partner.org}</h2>
                            <p>{partner.description}</p>
                            {#if partner.link != ""}
                            <a href="{partner.link}" target="_blank" style="color: var(--link-green); font-weight: bold">Donate</a>
                            {/if}
                        </div>
                    </div>
                </div>
                {/if}
            {/each}
            {/each}
        </div>
    </div>
</section>