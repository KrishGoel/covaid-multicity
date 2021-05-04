<script>
    // Params n dat
    export let params
    import {blogPosts} from '../blog.js'

    console.log(params.id)

    var postsList = [];
    for (var i = 0; i < blogPosts.length; i++) {
        postsList[i] = blogPosts[i].id
    }
    console.log(postsList)
    var id = params.id.toLowerCase()

    var postIndex = postsList.indexOf(id)

    var notionUrl = blogPosts[postIndex].notionID

    const fetchPost = (async () => {
        var response = await fetch('https://potion-api.vercel.app/html?id=' + notionUrl)
        return await response.text()
    })()
</script>

<section>
    <div class="width-restriction">
        {#await fetchPost}
        {:then data}
        {@html data}
        {:catch error}
        {/await}
    </div>

</section>