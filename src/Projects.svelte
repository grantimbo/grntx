<script>
    import { onMount } from 'svelte';
    import Modal from './Modal.svelte';

	let showModal = false;

    let projects = [];
    let ModalContents = [
        {title: null},
        {date: null},
        {content: null}
    ]

    onMount(async () => {
        const res = await fetch(`https://grantimbo.com/wp-json/wp/v2/posts`);
        projects = await res.json();
    });
</script>

<main>
    <h1>PROJECTS</h1>
    <p>Featured projects I’ve worked with.</p>
    <ul>
        <li>Featured</li>
        <li>3D Modelling</li>
        <li>Product Visualizations</li>
        <li>Web and Graphics</li>
        <li>Graphic Designs</li>
        <li>Motion Graphics</li>
    </ul>
    <div class="projects">

    {#each projects as project}

        <button on:click="{() => { 
            showModal = true, 
            ModalContents.title = project.title.rendered,
            ModalContents.date = project.date,
            ModalContents.content = project.content.rendered
        }}">
            <img src={project.thumbnail_url} alt={project.title.rendered}>
            <h2>{project.title.rendered}</h2>
            <span>{project.date}</span>
            <span>Tools</span>
            <ul>
                <li>Cinema 4D</li> 
                <li>After effects</li> 
            </ul>
        </button>

    {:else}
		<!-- this block renders when photos.length === 0 -->
		<p>loading...</p>
	{/each}

    {#if showModal}
        <Modal on:close="{() => showModal = false}">
            <h2 slot="header">{ModalContents.title}</h2>
            <p>{ModalContents.date}</p>
            <div class="content">{@html ModalContents.content}</div>
        </Modal>
    {/if}
   
    </div>
</main>

<style>
.projects {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 1rem;
}
.projects button {
		border: 1px solid #aaa;
		border-radius: 2px;
		box-shadow: 2px 2px 8px rgba(0,0,0,0.1);
		padding: 1em;
		margin: 0 0 1em 0;
	}
</style>