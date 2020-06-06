<script>
	import { Router, Route } from "svelte-routing";
	import Home from './pages/Home.svelte';
	import Projects from './pages/Projects.svelte';
	import Category from './pages/Category.svelte';
	import Services from './pages/Services.svelte';
	import About from './pages/About.svelte';
	import NotFound from './pages/NotFound.svelte';
	// import { onMount } from 'svelte';

	// let projects = [];
	
	// // production api
	let apiHost = `https://grantimbo.com/`;

	// onMount(async () => {
    //     const res = await fetch( apiHost + `grntx/api/collections/get/projects?token=account-ed31d41ed4c887f51e09ec138ace24`);
	// 	projects = await res.json();
	// 	projects = projects.entries;
	// });

	// // local api
	// let apiHost = `http://localhost/`;
	// onMount(async () => {
    //     const res = await fetch( apiHost + `cockpit/api/collections/get/projects`);
	// 	projects = await res.json();
	// 	projects = projects.entries;
	// });
	

</script>

<main>
	<Router>
		<Route path="/"><Home /></Route>
		<Route path="projects"><Projects {apiHost}/></Route>
		<Route path="project"><Category {apiHost}/></Route>
		<Route path="projects/:slug" let:params><Projects {apiHost} slug="{params.slug}"/></Route>
		<Route path="services"><Services/></Route>
		<Route path="about"><About/></Route>
		<Route><NotFound/></Route>
	</Router>
</main>