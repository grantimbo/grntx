<script>
	import Projects from './Projects.svelte';
	import Services from './Services.svelte';
	import About from './About.svelte';
	import { onMount } from 'svelte';

	let projects = [];
	let current = 'home';

	onMount(async () => {
        const res = await fetch(`https://grantimbo.com/wp-json/wp/v2/posts`);
        projects = await res.json();
    });

	
</script>

<main>
	
	<section>
		
		{#if current === 'home'}
			<div class="home">
				<h1>Hello</h1>
				<p>My name is Grant Imbo. I'm a multimedia artist creating cool stuff across the web and a developer focusing mainly on front-end.</p>
				<button on:click="{() => current = 'projects'}">Projects</button>
			</div>
		{/if}
		{#if current === 'projects'}
			<Projects {projects} />
		{/if}
		{#if current === 'services'}
			<Services/>
		{/if}
		{#if current === 'about'}
			<About/>
		{/if}

	</section>

	<nav>
		<button class="{current === 'home' ? 'active' : ''}" on:click="{() => current = 'home'}">
			<span>Home</span>
		</button>
		<button class="{current === 'projects' ? 'active' : ''}"	on:click="{() => current = 'projects'}">
			<span>Projects</span>
		</button>
		<button class="{current === 'services' ? 'active' : ''}"	on:click="{() => current = 'services'}">
			<span>Services</span>
		</button>
		<button class="{current === 'about' ? 'active' : ''}"	on:click="{() => current = 'about'}">
			<span>About</span>
		</button>
	</nav>


</main>

<style>
	:global(body) {
		background: #2b2b2b;
		color: #fff;
	}
	section .home {
		display: flex;
		align-items: center;
		height: 100vh;
		padding: 20%;
		box-sizing: border-box;
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
		background: #2b2b2b;
		border: 4px solid #fff;
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
	nav button.active:before,
	nav button:hover:before {
		background: #8AFF00;
		-webkit-transition: all .4s ease;
		-o-transition: all .4s ease;
		transition: all .4s ease;
	}
	nav button:after {
		background: #2B2B2B;
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
	nav button.active span,
	nav button:hover span {
		right: 80%;
	}
	nav span:before {
		content: "";
		position: absolute;
		left: -28px;
		top: 0;
		height: 0;
		width: 0;
		border-left: 14px solid transparent;
		border-top: 14px solid transparent;
		border-bottom: 14px solid transparent;
		border-right: 14px solid #fff;
	}
</style>