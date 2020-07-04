<script>
	import { Router, Route } from "svelte-routing";
	import Home from './pages/Home.svelte';
	import Projects from './pages/Projects.svelte';
	import Services from './pages/Services.svelte';
	import About from './pages/About.svelte';
	import NotFound from './pages/NotFound.svelte';
</script>

<Router>
	<Route path="/"><Home/></Route>
	<Route path="projects"><Projects/></Route>
	<Route path="projects/:slug" let:params><Projects slug="{params.slug}"/></Route>
	<Route path="services"><Services/></Route>
	<Route path="about"><About/></Route>
	<Route><NotFound/></Route>
</Router>