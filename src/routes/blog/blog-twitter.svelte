<script>
	const fetchPost = (async () => {
		var response = await fetch('https://potion-api.vercel.app/html?id=dc6dfef0945341358627210a5c622db9')
		return await response.text()
        // console.log(response)
	})()
</script>

<section>
    <div class="width-restriction">
        {#await fetchPost}
        <p>Blog post loading...</p>
        {:then data}
        {@html data}
        {:catch error}
        <p>Blog post could not be loaded</p>
        {/await}

    </div>
</section>

<!-- {@html card.paragraphText} -->