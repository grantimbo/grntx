<script>
    import Modal from '../components/Modal.svelte';
    import { projects } from "../_projects";
    import { navigate, Link } from "svelte-routing";

    export let apiHost;
    export let slug;

    let showModal = false;
    let post;

    // check if page has a slug
    if (slug) {
        let showModal = true;
        post = projects.find(p => p.slug == slug)

        if (!post) {
            navigate("/404", { replace: true });
        }
    }

    // replace url
    function replaceUrl(content) {
        let replace = 'src="/'
        let replaceWith = 'src="' + apiHost;
        let reg = new RegExp(replace, "g");
        let newContent = content.replace(reg, replaceWith)
        return newContent;
    }

</script>

<section class="wrap">
    <h1>Projects</h1>
    <p>Featured projects I’ve worked with.</p>

    <section class="projects-wrap">

    {#each projects as project}

        <Link to="/projects/{project.slug}">
            <figure>
                <div class="thumbnail">
                    <img src={project.thumbnail} alt={project.title}>
                </div>
                <div class="details">
                    <h3>{project.title}</h3>
                    <span>{project.date}</span>
                </div>
            </figure>
        </Link>

    {:else}
        <!-- this block renders when photos.length === 0 -->
        <p>loading projects...</p>
    {/each}
    
   
    </section>


    {#if post}

        <Modal on:close="{() => showModal = false}">
            <h2 slot="header">{post.title}</h2>
            <p>{post.date}</p>
            <div class="content">{@html replaceUrl(post.content)}</div>
        </Modal>

    {/if}
</section>

<style>
    h1 {
        margin: 0;
    }
    section.projects-wrap {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        grid-gap: 1rem;
        max-width: 1280px;
        margin: 40px auto 0;
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