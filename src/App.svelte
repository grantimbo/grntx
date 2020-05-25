<script>
	import Projects from './pages/Projects.svelte';
	import Services from './pages/Services.svelte';
	import About from './pages/About.svelte';
	import { onMount } from 'svelte';

	let projects = [];
	let current = 'home';
	let apiHost = `https://grantimbocom.ipage.com/`;

	onMount(async () => {
        const res = await fetch( apiHost + `grntx-api/api/collections/get/projects?token=account-ed31d41ed4c887f51e09ec138ace24`);
		projects = await res.json();
		projects = projects.entries;
	});
	
	let active = false;

	$: if (active == true) {
		setTimeout(function() {
			active = false;
		}, 1200)
	}

	function tae(e) {
		active = true;
		setTimeout(function() {
			current = e
		}, 1200);
	}

	
	
</script>

<main>
	<div class="transition" class:active={active}></div>
	<section>
		{#if current === 'home'}
			<div class="home">
				<h1>Hello</h1>
				<p>My name is Grant Imbo. I'm a multimedia artist creating cool stuff across the web and a developer focusing mainly on front-end.</p>
				<button on:click="{() => tae('projects')}">Projects</button>
			</div>
		{/if}
		{#if current === 'projects'}
			<Projects {projects} {apiHost}/>
		{/if}
		{#if current === 'services'}
			<Services/>
		{/if}
		{#if current === 'about'}
			<About/>
		{/if}
	</section>
</main>

<nav>
	<button class="{current === 'home' ? 'active' : ''}" on:click="{() => tae('home')}">
		<span>Home</span>
	</button>
	<button class="{current === 'projects' ? 'active' : ''}" on:click="{() => tae('projects')}">
		<span>Projects</span>
	</button>
	<button class="{current === 'services' ? 'active' : ''}" on:click="{() => tae('services')}">
		<span>Services</span>
	</button>
	<button class="{current === 'about' ? 'active' : ''}" on:click="{() => tae('about')}">
		<span>About</span>
	</button>
</nav>

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