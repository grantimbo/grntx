<script>
	import { Router, Route } from "svelte-routing";
	import Projects from './pages/Projects.svelte';
	import Project from './pages/Project.svelte';
	import Services from './pages/Services.svelte';
	import About from './pages/About.svelte';
	import Home from './pages/Home.svelte';
	import NavLink from './components/Navlink.svelte';
	import { onMount } from 'svelte';

	let projects = [];
	let activeSlug = null;
	
	// projection api
	// let apiHost = `https://grantimbocom.ipage.com/`;

	// onMount(async () => {
    //     const res = await fetch( apiHost + `grntx-api/api/collections/get/projects?token=account-ed31d41ed4c887f51e09ec138ace24`);
	// 	projects = await res.json();
	// 	projects = projects.entries;
	// });

	// local api
	let apiHost = `http://localhost/`;
	onMount(async () => {
        const res = await fetch( apiHost + `cockpit/api/collections/get/projects`);
		projects = await res.json();
		projects = projects.entries;
	});
	
	// let slug = null;

	

	export let url = "";

</script>

<main>
	<Router url="{url}">
		<Route path="/"><Home /></Route>
		<Route path="projects"><Projects {projects} {apiHost}/></Route>
		<Route path="projects/:slug" let:params><Project projects={projects} slug="{params.slug}"/></Route>
		<Route path="services"><Services/></Route>
		<Route path="about"><About/></Route>

		<nav>
			<NavLink to="/"><span>Home</span></NavLink>
			<NavLink to="projects"><span>Projects</span></NavLink>
			<NavLink to="services"><span>Services</span></NavLink>
			<NavLink to="about"><span>About</span></NavLink>
		</nav>
	</Router>
</main>