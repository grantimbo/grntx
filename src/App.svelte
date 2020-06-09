<script>
	import { Router, Route } from "svelte-routing";
	import Home from './pages/Home.svelte';
	import Projects from './pages/Projects.svelte';
	import Category from './pages/Category.svelte';
	import Services from './pages/Services.svelte';
	import About from './pages/About.svelte';
	import NotFound from './pages/NotFound.svelte';
	
	let apiHost = `https://grantimbo.com/`;

</script>

<main>
	<Router>
		<Route path="/"><Home /></Route>
		<Route path="projects"><Projects {apiHost}/></Route>
		<Route path="project-type/:cat" let:params><Category cat="{params.cat}"/></Route>
		<Route path="projects/:slug" let:params><Projects {apiHost} slug="{params.slug}"/></Route>
		<Route path="services"><Services/></Route>
		<Route path="about"><About/></Route>
		<Route><NotFound/></Route>
	</Router>
</main>