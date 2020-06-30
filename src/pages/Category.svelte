<script>
    import Modal from '../components/Modal.svelte';
    import CategoryNavBar from '../components/CategoryNavBar.svelte';
    import Navbar from '../components/NavBar.svelte';
    import { projects } from "../_projects";
    import { navigate, Link } from "svelte-routing";

    export let cat;

    let showModal = false;
    let post;
    
    // if single post
    if (cat) {
        showModal = true;
        post = projects.find(p => p.cat == cat);
    }

    $: postList = projects.filter(p => {
        return p.tags.find(c => c == cat)
    })

    function capitalizeFirstLetter(string) {
        return string.replace(/-/g, " ");
    }

</script>

<header>
    <Link to="/">
        <img class="logo" src="../imgs/logo.svg" alt="Grant Imbo">
    </Link>
    <Navbar/>
</header>
<CategoryNavBar/>
<section class="project-wrap">
    <h1>{capitalizeFirstLetter(cat)}</h1>

    <section class="projects-list">

    {#each postList as project}

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
            <h2 slot="header">{post.title}</h2>
            <p>{post.date}</p>
            <div class="content">{@html post.content}</div>
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
        text-transform: capitalize;
    }
    .project-wrap p {
        margin-bottom: 1.2rem;
    }
    h3 {
        margin: 0;
    }

    @media (min-width: 992px) {
        .project-wrap {
            padding-left: 204px;
            padding-right: 20px;
        }
    }
</style>