<script>

	// Routing 
	import router from "page"
	let page
	let params
	
	import Index from './routes/Index.svelte'
	import About from './routes/About.svelte'
	import Volunteer from './routes/Volunteer.svelte'
	import Donate from './routes/Donate.svelte'
	import Partners from './routes/Partners.svelte'
	import Verification from './routes/Verification.svelte'
	
	router('/', () => (page = Index))
	router('/about', () => (page = About))
	router('/volunteer', () => (page = Volunteer))
	router('/donate', () => (page = Donate))
	router('/partners', () => (page = Partners))
	router('/verification', () => (page = Verification))

	// City routing
	import City from './routes/CityResources.svelte'
	router(
		'/city/:city',
		(ctx, next) => {
			params = ctx.params
			next()
		},
		() => (page = City)
	)

	// Blog routing
	import Blog from './routes/Blog.svelte'
	router('/blog', () => (page = Blog))

	import BlogPost from "./routes/BlogPost.svelte"
	router(
		'/blog/:id',
		(ctx, next) => {
			params = ctx.params
			next()
		},
		() => (page = BlogPost)

	)
	
	router.start()

	import Nav from "../components/Nav.svelte"
	import Footer from "../components/Footer.svelte"

</script>

<Nav/>

<br/><br/>

<svelte:component this="{page}" params="{params}"/>

<br/><br/>

<Footer/>