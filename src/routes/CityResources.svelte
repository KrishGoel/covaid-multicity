<script>
    // Range
    import {range} from '../range.js'
    let errorMessage = "Potion failed"
    // Params n dat
    export let params
    
    import {cities} from '../cities.js'
    var citiesList = [];
    for (var i = 0; i < cities.length; i++) {
        citiesList[i] = cities[i].city
    }
    
    var city = params.city.toLowerCase()
    
    let cityExists = true
    if (!citiesList.includes(city)) {
        // City doesnot exist
        cityExists = false
        console.log('City doesnot exist')
    }
    // City exists
    var cityIndex = citiesList.indexOf(city)
    
    city = cities[cityIndex].displayName
    // console.log(cities[cityIndex])
    // Needs
    let oxygenBed = false
    let icu = false
    let ventilator = false
    let plasma = false
    let cylinder = false
    let concentrator = false
    let remdesivir = false
    let tocilizumab = false
    let itolizumab = false
    let ivermectin = false
    let methylprednisolone = false
    let fabiflu = false
    let dexamethasone = false
    let doctor = false
    let homeicu = false
    let food = false
    // Potion fetch reqs
    const fetchOxygenBed = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.oxygenBed)
        return await response.json()
    })()
    const fetchICU = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.icu)
        return await response.json()
    })()
    const fetchVentilator = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.ventilator)
        return await response.json()
    })()
    const fetchPlasma = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.plasma)
        return await response.json()
    })()
    const fetchCylinder = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.cylinder)
        return await response.json()
    })()
    const fetchConcentrator = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.concentrator)
        return await response.json()
    })()
    const fetchRemdesivir = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.remdesivir)
        return await response.json()
    })()
    const fetchTocilizumab = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.tocilizumab)
        return await response.json()
    })()
    const fetchItolizumab = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.itolizumab)
        return await response.json()
    })()
    const fetchIvermectin = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.ivermectin)
        return await response.json()
    })()
    const fetchMethylprednisolone = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.methylprednisolone)
        return await response.json()
    })()
    const fetchFabiflu = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.fabiflu)
        return await response.json()
    })()
    const fetchDexamethasone = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.dexamethasone)
        return await response.json()
    })()
    const fetchDoctor = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.doctor)
        return await response.json()
    })()
    const fetchHomeICU = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.homeicu)
        return await response.json()
    })()
    const fetchFood = (async () => {
        var response = await fetch('https://potion-api.vercel.app/table?id=' + cities[cityIndex].db.food)
        return await response.json()
    })()
    // Twitter Bot
    var search;
    var query;
    function twitterDeploy(cityName) {
        search = []
        query = "https://twitter.com/search?q=verified+" + cityName + "+"
        var needs = [
            {
                "name": "Oxygen Bed",
                "need": oxygenBed,
                "query": "bed+OR+oxygen+bed"
            },
            {
                "name": "ICU",
                "need": icu,
                "query": "icu+OR+icu+bed"
            },
            {
                "name": "Ventilator",
                "need": ventilator,
                "query": "bed+OR+ventilator"
            },
            {
                "name": "Plasma Donor",
                "need": plasma,
                "query": "plasma+OR+plasma+donor"
            },
            {
                "name": "Oxygen Cylinder",
                "need": cylinder,
                "query": "oxygen+OR+oxygen+cylinder"
            },
            {
                "name": "Oxygen Concentrator",
                "need": concentrator,
                "query": "(oxygen+concentrator)+OR+concentrator"
            },
            {
                "name": "Remdesivir",
                "need": remdesivir,
                "query": "remdesivir"
            },
            {
                "name": "Tocilizumab",
                "need": tocilizumab,
                "query": "tocilizumab"
            },
            {
                "name": "Itolizumab",
                "need": itolizumab,
                "query": "itolizumab"
            },
            {
                "name": "Doctor",
                "need": doctor,
                "query": "doctor"
            },
            {
                "name": "Ivermectin",
                "need": ivermectin,
                "query": "ivermectin"
            },
            {
                "name": "Methylprednisolone",
                "need": methylprednisolone,
                "query": "methylprednisolone+OR+(methyl+prednisolone)"
            },
            {
                "name": "FabiFlu",
                "need": fabiflu,
                "query": "fabiflu+OR+fabi+flu+OR++favipiravir"
            },
            {
                "name": "Dexamethasone",
                "need": dexamethasone,
                "query": "dexamethasone+OR+dexa+methasone"
            },
            {
                "name": "Home ICU",
                "need": homeicu,
                "query": "(home+icu)+OR+(home+nursing)"
            },
            {
                "name": "Food Service",
                "need": food,
                "query": "(home+food)+OR+(home+service)+OR(food+service)"
            }
        ]
        for (var i = 0; i < needs.length; i++) {
            if (needs[i].need == true) {
                search[search.length] = i
            }
        }
        for (var j = 0; j < search.length; j++) {
            if ((search.length == 1) || (j == (search.length - 1))) {
                query += needs[search[j]].query + "+"
            } else {
                query += needs[search[j]].query + "+OR+"
            }
        }
    
        query += `-"not+verified"+-"unverified"+-"needed"+-"need"+-"required"+-"urgent"+-"asap"+-"urgently"&f=live`
        console.log("Query: " + query)
        window.open(query, '_blank').focus()
        console.log("Twitter search deployed")
    }
    // To call, use twitterDeploy(city)
    // var showDB = false
    var showDB = true //Make this false
    function showDBNow() {
        showDB = true
    }
    // Tweet for help
    function tweetForHelp(cityName){
        window.open(("https://twitter.com/intent/tweet?text=Hey%20@CovAID_support,%20I%20need%20insertResourceHere%20in%20"+cityName+".%20This%20is%20an%20SOS!"), '_blank').focus()
    }
    // Instagram DM Helpline
    function dmHelpline() {
        window.open("https://instagram.com/covaid.resources", "_blank").focus()
    }
</script>

<section>
    <div class="width-restriction">
        {#if cityExists}
        
        
        <h1>{city}</h1>
        <button on:click={dmHelpline}>
            <h5>Instagram DM Helpline</h5>
        </button>
        <button on:click={tweetForHelp(city)}>
            <h5>Tweet for help</h5>
        </button>

        <br/><br/>
        
        <div class="row">
            <!-- 1st Column -->
            <div class="col-3">
                <div class="card">
                    <div class="width-restriction">
                        <h2>🏥 Beds</h2>
                        <br/>
                        <!-- Oxygen bed checkbox -->
                        <input type=checkbox id="oxygenBed" bind:checked={oxygenBed}/>
                        <label for="oxygenBed">
                            Bed with Oxygen
                        </label><br/>

                        <!-- ICU checkbox -->
                        <input type=checkbox id="icu" bind:checked={icu}/>
                        <label for="icu">
                            Bed with ICU
                        </label><br/>

                        <!-- Ventilator checkbox -->
                        <input type=checkbox id="ventilator" bind:checked={ventilator}/>
                        <label for="ventilator">
                            Bed with Ventilator
                        </label><br/>
                    </div>
                </div>

                <div class="card">
                    <div class="width-restriction">
                        <h2>🩸 Plasma</h2>
                        <br/>
                        <!-- Plasma checkbox -->
                        <input type=checkbox id="plasma" bind:checked={plasma}/>
                        <label for="plasma">
                            Plasma Donors
                        </label><br/>
                    </div>
                </div>
                <!-- <br/> -->
                

            </div>

            <!-- 2nd Column -->
            <div class="col-3">

                <div class="card">
                    <div class="width-restriction">
                        <h2>😷 Oxygen</h2>
                        <br/>
                        <!-- Cylinder checkbox -->
                        <input type=checkbox id="cylinder" bind:checked={cylinder}/>
                        <label for="cylinder">
                            Oxygen Cylinder
                        </label><br/>
                        <!-- Concentrator checkbox -->
                        <input type=checkbox id="concentrator" bind:checked={concentrator}/>
                        <label for="concentrator">
                            Oxygen Concentrator
                        </label><br/>
                    </div>
                </div>


                <!-- <div class="card">
                    <div class="width-restriction">
                        <h2>💊 Injections</h2>
                        <br/>
                        Remdesivir checkbox
                        <input type=checkbox id="remdesivir" bind:checked={remdesivir}/>
                        <label for="remdesivir">
                            Remdesivir
                        </label><br/>
                        Tocilizumab checkbox
                        <input type=checkbox id="tocilizumab" bind:checked={tocilizumab}/>
                        <label for="tocilizumab">
                            Tocilizumab
                        </label><br/>
                        Itolizumab checkbox
                        <input type=checkbox id="itolizumab" bind:checked={itolizumab}/>
                        <label for="itolizumab">
                            Itolizumab
                        </label><br/>
                        
                    </div>
                </div> -->

                <div class="card">
                    <div class="width-restriction">
                        <h2>💊 Medicines</h2>
                        <br/>
                        <!-- Ivermectin checkbox -->
                        <input type=checkbox id="ivermectin" bind:checked={ivermectin}/>
                        <label for="ivermectin">
                            Ivermectin
                        </label><br/>
    
                        <!-- Methylprednisolone checkbox -->
                        <input type=checkbox id="methylprednisolone" bind:checked={methylprednisolone}/>
                        <label for="methylprednisolone">
                            Methylprednisolone
                        </label><br/>
    
                        <!-- FabiFlu checkbox -->
                        <input type=checkbox id="fabiflu" bind:checked={fabiflu}/>
                        <label for="fabiflu">
                            FabiFlu/Favipiravir
                        </label><br/>

                        <!-- Dexamethasone checkbox -->
                        <input type=checkbox id="dexamethasone" bind:checked={dexamethasone}/>
                        <label for="dexamethasone">
                            Dexamethasone
                        </label><br/>
                        
                    </div>
                </div>
                
            </div>
            
            <!-- 3rd Column -->
            <div class="col-3">
                {#if city != "Delhi"}
                <div class="card">
                    <div class="width-restriction">
                        <h2>🩺 Doctor's Opinion</h2>
                        <br/>
                        <!-- Doctor checkbox -->
                        <input type=checkbox id="doctor" bind:checked={doctor}/>
                        <label for="doctor">
                            Doctor
                        </label><br/>
                        
                    </div>
                </div>
                {/if}

                <div class="card">
                    <div class="width-restriction">
                        <h2>🏡 Home ICU</h2>
                        <br/>
                        <!-- Home ICU checkbox -->
                        <input type=checkbox id="homeicu" bind:checked={homeicu}/>
                        <label for="homeicu">
                            Home ICU
                        </label><br/>
                        
                    </div>
                </div>

                {#if city != "Delhi"}
                <div class="card">
                    <div class="width-restriction">
                        <h2>🍴 Food Services</h2>
                        <br/>
                        <!-- Food Services checkbox -->
                        <input type=checkbox id="food" bind:checked={food}/>
                        <label for="food">
                            Food Services
                        </label><br/>
                        
                    </div>
                </div>

                {:else}
                <br/>
                <p>
                    For doctor consultations, food services and testing centres in Delhi, please visit our partner website
                </p>
                <a href="https://www.covinfo.net/" target="_blank">
                    <button>
                        <h5>CoVinfo.net</h5>
                    </button>
                </a>


                {/if}

            </div>
            
        </div>

        <br/><br/>
        
        <button on:click={showDBNow}>
            <h5>Search verified leads on our database</h5>
        </button>

        <button on:click={twitterDeploy(city)}>
            <h5>Search the latest leads on Twitter</h5>
        </button>

        <br/><br/>

        <p>
            Note: According to a recent provision passed by the Government, Remdesivir and Tocilizumab are to be administered by hospitals and their authorised dealers ONLY. Thus we have removed the filter for the same. 
            <br/>
            For further information, or updates on availability of the injections, kindly DM us via &nbsp;
            <a href="https://twitter.com/covaid_support" target="_blank">Twitter @CovAID_support</a> &nbsp; or &nbsp;<a href="https://www.instagram.com/covaid.resources/" target="_blank">Instagram @covaid.resources</a>.
        </p>

        <br/><br/>

        {#if showDB}
        <h1>Resources from our personally-verified database</h1>
        <br/>

        <!-- Oxygen Bed DB -->
        {#if oxygenBed}
            <h2>Hospital beds with Oxygen</h2>
            {#await fetchOxygenBed}
            <p>Hospital Beds with Oxygen loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- ICU DB -->
        {#if icu}
            <h2>Hospital beds with ICU</h2>
            {#await fetchICU}
            <p>Hospital Beds with ICU loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Ventilator DB -->
        {#if ventilator}
            <h2>Hospital beds with Ventilator</h2>
            {#await fetchVentilator}
            <p>Hospital Beds with Ventilator loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Plasma DB -->
        {#if plasma}
            <h2>Plasma donors</h2>
            {#await fetchPlasma}
            <p>Plasma donors loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Cylinder DB -->
        {#if cylinder}
            <h2>Oxygen Cylinders</h2>
            {#await fetchCylinder}
            <p>Oxygen Cylinders loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Concentrator DB -->
        {#if concentrator}
            <h2>Oxygen Concentrators</h2>
            {#await fetchCylinder}
            <p>Oxygen Concentrators loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Remdesivir DB -->
        <!-- {#if remdesivir}
            <h2>Remdesivir</h2>
            {#await fetchRemdesivir}
            <p>Remdesivirs loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if} -->

        <!-- Tocilizumab DB -->
        <!-- {#if tocilizumab}
            <h2>Tocilizumab</h2>
            {#await fetchTocilizumab}
            <p>Tocilizumabs loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if} -->

        <!-- Itolizumab DB -->
        <!-- {#if itolizumab}
            <h2>Itolizumab</h2>
            {#await fetchItolizumab}
            <p>Itolizumabs loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if} -->

        <!-- Ivermectin DB -->
        {#if ivermectin}
            <h2>Ivermectin</h2>
            {#await fetchIvermectin}
            <p>Ivermectins loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Methylprednisolone DB -->
        {#if methylprednisolone}
            <h2>Methylprednisolone</h2>
            {#await fetchMethylprednisolone}
            <p>Methylprednisolones loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Fabiflu DB -->
        {#if fabiflu}
            <h2>FabiFlu/Favipiravir</h2>
            {#await fetchFabiflu}
            <p>FabiFlus loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Dexamethasone DB -->
        {#if dexamethasone}
            <h2>Dexamethasone</h2>
            {#await fetchDexamethasone}
            <p>Dexamethasone loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Doctor DB -->
        {#if doctor}
            <h2>Doctors</h2>
            {#await fetchDoctor}
            <p>Doctors loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- HomeICU DB -->
        {#if homeicu}
            <h2>Home ICU & Nursing Services</h2>
            {#await fetchHomeICU}
            <p>Home ICUs loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        <!-- Food Services DB -->
        {#if food}
            <h2>Food Services</h2>
            {#await fetchFood}
            <p>Food Services loading...</p>
            {:then data}
            <div class="row">
                {#each range(0,3,1) as i, index}
                <div class="col-3">
                    {#each data as lead, j}
                    {#if lead.fields.available}
                    {#if j%3 == i}
                    <div class="card">
                        <div class="width-restriction">
                            <h2>{lead.fields.name}</h2>
                            <h5><strong>Last checked:</strong> {lead.fields.timestamp}</h5>
                            <br/>
                            <p>📍 {lead.fields.location}</p>
                            <p>📞 
                                <a href="tel: {lead.fields.contact}">
                                    {lead.fields.contact}
                                </a>
                            </p>
                            <br/>
                            {#if lead.fields.notes != undefined}
                            <p>
                                {@html lead.fields.notes}
                            </p>
                            {/if}
                        </div>
                    </div>
                    {/if}
                    {/if}
                    {/each}
                </div>
                {/each}
            </div>
            {:catch error}
            <p>{errorMessage}</p>
            {/await}
        {/if}

        {/if}


        {:else}


        <h2>City doesnot exist, kindly head back to the <a href="/">home page</a></h2>
        
        
        {/if}
    </div>
</section>