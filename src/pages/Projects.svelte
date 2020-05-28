<script>
    import Modal from '../components/Modal.svelte';
    // import Project from '../components/Project.svelte';
    import { navigate, Link } from "svelte-routing";


	let showModal = false;
    let ModalContents = [
        {title: null},
        {thumbnail: null},
        {content: null},
        {slug: null}
    ]

    export let projects;
    export let apiHost;

    function changeUrl() {
        console.log('test');
        
    };

    function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
    console.log(location)
    console.log(href)
    console.log(isPartiallyCurrent)
    console.log(isCurrent)
  }

    
</script>

<section class="wrap">
    <h1>PROJECTS</h1>
    <p>Featured projects I’ve worked with.</p>

    <section class="projects-wrap">

    {#each projects as project}

        <Link to="/projects/{project.slug}" state="hello world">
            {project.title}
        </Link>

        <!-- <figure on:click="{() => {
                showModal = true, 
                ModalContents.title = project.title,
                ModalContents.published = project.published,
                ModalContents.content = project.content


                changeUrl()
            }}">
            <div class="thumbnail">
                <img src={apiHost + project.thumbnail.path} alt={project.title}>
            </div>
            <div class="details">
                <h3>{project.title}</h3>
                <span>{project.published}</span>
            </div>
        </figure> -->

    {:else}
		<!-- this block renders when photos.length === 0 -->
		<p>loading projects...</p>
	{/each}

    {#if showModal}
        <Modal on:close="{() => showModal = false}">
            <h2 slot="header">{ModalContents.title}</h2>
            <p>{ModalContents.published}</p>
            <div class="content">{@html ModalContents.content}</div>
        </Modal>
    {/if}
   
    </section>
</section>

<style>
section.projects-wrap {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    grid-gap: 1rem;
    max-width: 1280px;
    margin: 0 auto;
}
figure {
    border-radius: 4px;
    overflow: hidden;
    position: relative;
    margin: 0;
    padding: 0;
}
.thumbnail {
    position: relative;
    overflow: hidden;
    border: 1px solid #212528;
    background: #161a1f;
    height: 210px;
}
img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.details {
    position: absolute;
    bottom: 0;
    width: 100%;
    padding: 1rem;
}






</style>