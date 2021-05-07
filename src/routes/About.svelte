<script>
    import {range} from '../range'

    const fetchVolunteers = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=77f31dccce1143e197353657fd2d7fce')
        return await response.json()
    })()
</script>

<style>
    .card p {
    margin-bottom: 0;
    }
 </style>
 
 <section>
    <div class="width-restriction">
       <div class="width-restriction">
          <h1>About Us</h1>
          <p>
             CovAID is the joint <strong>initiative of 5 students from Sanskriti School, New Delhi</strong>. We have initiated a unified <strong>online platform for smooth and accurate dispersal of information</strong> regarding availability of Covid-19 resources in the National Capital Region. <strong>Verification takes place through direct contact (calls, messages, etc.) that involves pictorial proof</strong>. These verified updates are then posted on the platform at frequent, regular intervals.
             <br><br>
             Alongside this, we have also be <strong>created a filter for conveniently searching Twitter updates regarding COVID-19 resources</strong> and availability. The nation has lost many lives due to inaccurate information dispersal. With our initiative, we hope to overcome this hurdle. 
             <br><br>
             CovAID is simply a medium to connect the users to suppliers and <strong>does not participate in monetary transactions whatsoever i.e. it is a non-profit organisation</strong>. As the youth of India, we believe it is our duty to help all those that have been affected by the pandemic, whether they're our peers or elders. It is this beautiful country that we will inherit, and we must protect the tree whose roots have snuggled our childhoods.
             <br><br>
             Regards,
             <br>
             Team CovAID
          </p>
          <div class="row">
             <div class="col-3">
                <div class="card">
                   <div class="width-restriction">
                      <h3>Advait Roy</h3>
                      <p>Content Curation</p>
                   </div>
                </div>
                <div class="card">
                   <div class="width-restriction">
                      <h3>Srijan Tripathi</h3>
                      <p>Social Media and Outreach</p>
                   </div>
                </div>
             </div>
             <div class="col-3">
                <div class="card">
                   <div class="width-restriction">
                      <h3>Ishaan Kanudia</h3>
                      <p>Volunteer Affairs</p>
                   </div>
                </div>
                <div class="card">
                   <div class="width-restriction">
                      <h3>Raghav Sarangi</h3>
                      <p>Professional Executive</p>
                   </div>
                </div>
             </div>
             <div class="col-3">
                <div class="card">
                   <div class="width-restriction">
                      <h3>Krish Goel</h3>
                      <p>Tech Lead</p>
                   </div>
                </div>
             </div>
          </div>

          <br/>

          <h2>Team CovAID</h2>
          {#await fetchVolunteers}
            <p>Volunteers loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as volunteeer, j}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h3>{volunteeer.fields.name}</h3>
                            <p>{volunteeer.fields.role}</p>
                        </div>
                    </div>
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}

            <br/>
            <h2>Disclaimer</h2>
            <p>We would like to emphasize that the CovAID team does not take responsibility for the transactions that occur through these leads. No verification process is 100% infallible and there is always a risk for suppliers being fraudulent. We request all users to exercise the requisite discretion to maintain their own safety and security. Rest assured, CovAID is working to the best of its abilities to provide verified, real-time information to those in need.</p>
       </div>
    </div>
 </section>