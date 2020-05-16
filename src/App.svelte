<script>

	let current = 'home';

	import Projects from './Projects.svelte';
	import Services from './Services.svelte';
	import About from './About.svelte';
</script>

<main>
	
	<section>
		
		{#if current === 'home'}
			<div class="home">
				<div>
					<h1>Hello</h1>
					<p>My name is Grant Imbo. I'm a multimedia artist creating cool stuff across the web and a developer focusing mainly on front-end.</p>
					<button on:click="{() => current = 'projects'}">Projects</button>
				</div>
			</div>
		{/if}
		{#if current === 'projects'}<Projects/>{/if}
		{#if current === 'services'}<Services/>{/if}
		{#if current === 'about'}<About/>{/if}

	</section>

	<nav>
		<button class="{current === 'home' ? 'active' : ''}" on:click="{() => current = 'home'}">Home</button>
		<button class="{current === 'projects' ? 'active' : ''}"	on:click="{() => current = 'projects'}">Projects</button>
		<button class="{current === 'services' ? 'active' : ''}"	on:click="{() => current = 'services'}">Services</button>
		<button class="{current === 'about' ? 'active' : ''}"	on:click="{() => current = 'about'}">About</button>
	</nav>


</main>

<style>
	section .home {
		display: flex;
		align-items: center;
		height: 100vh;
		padding: 20%;
		box-sizing: border-box;
	}
	button {
		display: block;
	}

	.active {
		background-color: #ff3e00;
		color: white;
	}
	nav {
		position: fixed;
		top: 40%;
		right: 1rem;
	}
</style>