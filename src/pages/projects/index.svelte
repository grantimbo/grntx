<script>
    // import Modal from '../components/Modal.svelte';
    import { onMount } from 'svelte';
    import { url } from '@sveltech/routify';

	let projects = [];
	
	// production api
	let apiHost = `https://grantimbo.com/`;

	onMount(async () => {
        const res = await fetch( apiHost + `grntx/api/collections/get/projects?token=account-ed31d41ed4c887f51e09ec138ace24`);
		projects = await res.json();
		projects = projects.entries;
	});

	// // local api
	// let apiHost = `http://localhost/`;
	// onMount(async () => {
    //     const res = await fetch( apiHost + `cockpit/api/collections/get/projects`);
	// 	projects = await res.json();
	// 	projects = projects.entries;
	// });


    // let showModal = false;

    // replace url
    // function replaceUrl(content) {
    //     let replace = 'src="/'
    //     let replaceWith = 'src="' + apiHost;
    //     let reg = new RegExp(replace, "g");
    //     let newContent = content.replace(reg, replaceWith)
    //     return newContent;
    // }

</script>

<section class="wrap">
    <h1>PROJECTS</h1>
    <p>Featured projects I’ve worked with.</p>

    <section class="projects-wrap">

    {#each projects as project}

        <a href={$url('/projects/:slug', {slug: project.slug})}>
            <figure>
                <div class="thumbnail">
                    <img src={apiHost + project.thumbnail.path} alt={project.title}>
                </div>
                <div class="details">
                    <h3>{project.title}</h3>
                    <span>{project.published}</span>
                </div>
            </figure>
        </a>

    {:else}
        <!-- this block renders when photos.length === 0 -->
        <p>loading projects...</p>
    {/each}
    
   
    </section>


    <!-- {#if slug}

        <Modal on:close="{() => showModal = false}">
            <h2 slot="header">{post.title}</h2>
            <p>{post.published}</p>
            <div class="content">{@html replaceUrl(post.content)}</div>
        </Modal>

    {/if} -->
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
        height: 180px;
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
        background: linear-gradient(0deg, #000000b8, transparent);
        color: #fff;
    }
    .details h3 {
        margin-bottom: 0;
        font-size: 16px;
        font-weight: bold;
    }
    .details span {
        font-size: 12px;
    }
</style>