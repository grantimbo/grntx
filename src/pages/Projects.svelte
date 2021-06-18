<script>
    import Modal from '../components/Modal.svelte';
    import Navbar from '../components/NavBar.svelte';
    import { projects } from "../_projects";
    import { Link } from "svelte-routing";
    import { fly } from 'svelte/transition';
    import Lazy from 'svelte-lazy';

    export let slug;
		
    let showModal;
    !slug ? showModal = false : showModal = true
    
</script>


<header>
    <Link to="/">
        <img class="logo" src="/imgs/logo.svg" alt="Grant Imbo">
    </Link>
    <Navbar/>
</header>
<section class="project-wrap">
    <div class="project-head">
        <h2 in:fly={{y: 20, duration: 1000}}>Personal Projects</h2>
        <p in:fly={{y: 20, duration: 1000, delay:200}}>Shoot me an email if you wish to view my full portfolio</p>
    </div>
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

    {/each}
    
   
    </section>


    {#if showModal}
        <Modal on:close="{() => showModal = false}" slug={slug}/>
    {/if}
</section>


<style>

    .project-wrap {
        padding: 10px;
    }
    .project-head {
        text-align: center;
        max-width: 500px;
        width: 100%;
        margin: 2rem auto 3rem;
    }
    h3 {
        margin: 0;
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