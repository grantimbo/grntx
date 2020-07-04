<script>
    import Modal from '../components/Modal.svelte';
    import Navbar from '../components/NavBar.svelte';
    import { projects } from "../_projects";
    import { Link } from "svelte-routing";
    import Lazy from 'svelte-lazy';

    export let slug;

    let currentTab = 'featured';
    let showModal = false;
    let post;
    
    // if single post
    if (slug) {
        showModal = true;
        post = projects.find(p => p.slug == slug);

        if (!post) {
            window.location.href = window.location.origin + "/404";
        }
    }

    
</script>


<header>
    <Link to="/">
        <img class="logo" src="/imgs/logo.svg" alt="Grant Imbo">
    </Link>
    <Navbar/>
</header>
<section class="project-wrap">
    <h2>Featured Projects</h2>

    <section class="projects-list">

    {#each projects as project}

        <Link to="/projects/{project.slug}">
            <figure>
                <div class="thumbnail">
                    <Lazy offset={150} fadeOption={null}>
                        <img src={project.thumbnail} alt={project.title}>
                    </Lazy>
                </div>
                <div class="details">
                    <h3>{project.title}</h3>
                    <span>
                        {#each project.tags as tag}
                            <i class="{tag}"></i>
                        {/each}
                    </span>
                </div>
            </figure>
        </Link>

    {:else}
        <!-- this block renders when photos.length === 0 -->
        <p>No projects found</p>
    {/each}
    
   
    </section>


    {#if post}

        <Modal on:close="{() => showModal = false}">
            <div slot="header">
                <h3>{post.title}</h3>
                <p class="date">{post.date}</p>
            </div>
            <div slot="content">{@html post.content}</div>
        </Modal>

    {/if}
</section>


<style>

    .project-wrap {
        padding: 10px;
    }
    
    h3 {
        margin: 0;
    }
    p.date {
        font-size: .8rem;
    }
    .details {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .details i {
        font-size: 1rem;
        margin-right: 0.4rem;
    }
    .details i:last-child {
        margin-right: 0;
    }

    @media (min-width: 1280px) {
        .project-wrap {
            max-width: 1600px;
            margin: 0 auto;
        }
    }
</style>