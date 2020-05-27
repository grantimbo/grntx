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
	let apiHost = `https://grantimbocom.ipage.com/`;

	onMount(async () => {
        const res = await fetch( apiHost + `grntx-api/api/collections/get/projects?token=account-ed31d41ed4c887f51e09ec138ace24`);
		projects = await res.json();
		projects = projects.entries;
	});

	export let url = "";

	
	
</script>

<main>
	<Router url="{url}">
		<Route path="/"><Home /></Route>
		<Route path="projects"><Projects {projects} {apiHost}/></Route>
		<Route path="projects/:slug"><Project/></Route>
		<Route path="services"><Services/></Route>
		<Route path="about"><About/></Route>

		<nav>
			<NavLink to="/">Home</NavLink>
			<NavLink to="projects">Projects</NavLink>
			<NavLink to="services">Services</NavLink>
			<NavLink to="about">About</NavLink>
		</nav>
	</Router>
</main>


<style>
	main {
		position:relative;
		height: 100vh;
		overflow: hidden;
	}
	section .home {
		text-align: center;
		max-width: 500px;
		margin: 0 auto;
	}
	nav {
		position: fixed;
		top: 40%;
		right: 4px;
		z-index: 2;
		width: 64px;
	}
	nav button {
		position: relative;
		display: block;
		min-width: 54px;
		border: 0;
		outline: 0;
		background: none;
		cursor: pointer;
	}
	nav button:before {
		border-radius: 50%;
		background: #140f27;
		border: 2px solid #05ece7;
		width: 45px;
		height: 45px;
		display: block;
		content: "";
		z-index: 1;
		position: relative;
		-webkit-transition: all .4s ease;
		-o-transition: all .4s ease;
		transition: all .4s ease;
	}
	nav button:nth-child(2):before {
		border-color: #20a7ec;
	}
	nav button:nth-child(3):before {
		border-color: #3f52f3;
	}
	nav button:nth-child(4):before {
		border-color: #5c02f4;
	}
	nav button.active:before,
	nav button:hover:before {
		background: rgb(100,28,193);
		-webkit-transition: all .4s ease;
		-o-transition: all .4s ease;
		transition: all .4s ease;
	}
	nav button:after {
		background: #140f27;
		position: absolute;
		height: 100%;
		width: 100px;
		right: -80px;
		content: "";
		top: 0;
	}
	nav span {
		display: block;
		position: absolute;
		right: -130%;
		top: 17px;
		background: #fff;
		color: #000;
		font-size: 18px;
		padding: 2px 20px 2px 10px;
		z-index: 0;
		-webkit-transition: all .4s ease;
		-moz-transition: all .4s ease;
		-o-transition: all .4s ease;
		-ms-transition: all .4s ease;
		transition: all .4s ease;
	}
	nav button:hover span {
		right: 75%;
	}
	nav span:before {
		content: "";
		position: absolute;
		left: -28px;
		top: 0;
		height: 0;
		width: 0;
		border-left: 14px solid transparent;
		border-top: 14px solid #fff;
		border-bottom: 14px solid transparent;
		border-right: 14px solid #fff;
	}
</style>