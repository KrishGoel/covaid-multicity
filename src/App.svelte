<script>

	// Routing 
	import router from "page"
	let page
	let params
	
	import Index from './routes/Index.svelte'
	import About from './routes/About.svelte'
	import Volunteer from './routes/Volunteer.svelte'
	
	router('/', () => (page = Index))
	router('/about', () => (page = About))
	router('/volunteer', () => (page = Volunteer))

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
	
	router.start()

	import Nav from "../components/Nav.svelte"
	import Footer from "../components/Footer.svelte"

</script>

<Nav/>

<br/><br/>

<svelte:component this="{page}" params="{params}"/>

<br/><br/>

<Footer/>