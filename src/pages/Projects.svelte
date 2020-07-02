<script>
    import Modal from '../components/Modal.svelte';
    import Navbar from '../components/NavBar.svelte';
    import CategoryNavBar from '../components/CategoryNavBar.svelte';
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
<CategoryNavBar/>
<section class="project-wrap">
    <h1>Featured Projects</h1>
    <p>A few selected projects</p>

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
                    <!-- <span>{project.date}</span> -->
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
    header {
        position: fixed;
        top: 0;
        width: 100%;
        z-index: 2;
    }
    .project-wrap {
        padding: 80px 10px 80px 60px;
    }
    .project-wrap h1 {
        margin-bottom: 0;
    }
    .project-wrap p {
        margin-bottom: 1.2rem;
    }
    h3 {
        margin: 0;
    }
    p.date {
        font-size: .8rem;
    }

    @media (min-width: 992px) {
        .project-wrap {
            padding-left: 204px;
            padding-right: 20px;
        }
    }
</style>