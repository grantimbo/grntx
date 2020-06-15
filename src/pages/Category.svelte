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
        return string.charAt(0).toUpperCase() + string.slice(1);
    }


    

</script>

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

<Navbar/>

<style>
    .project-wrap {
        background: #F2F2F2;
        padding-bottom: 80px;
        min-height: 100vh;
    }
</style>