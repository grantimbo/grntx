<script>
    import Modal from '../components/Modal.svelte';
    import Navbar from '../components/NavBar.svelte';
    import CategoryNavBar from '../components/CategoryNavBar.svelte';
    import { projects } from "../_projects";
    import { navigate, Link } from "svelte-routing";

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

<CategoryNavBar/>

<section class="project-wrap">
    <h1>Featured Projects</h1>
    <p>Selected artworks i've worked with.</p>

    <section class="projects-list">

    {#each projects as project}

        <Link to="/projects/{project.slug}">
            <figure>
                <div class="thumbnail">
                    <img src={project.thumbnail} alt={project.title}>
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

<Navbar/>

<style>
    .project-wrap {
        background: #F2F2F2;
        padding-bottom: 80px;
    }
    h3 {
        margin: 0;
    }
    p.date {
        font-size: .8rem;
    }
</style>