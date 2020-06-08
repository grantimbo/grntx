<script>
    import Modal from '../components/Modal.svelte';
    import { projects } from "../_projects";
    import { navigate, Link } from "svelte-routing";

    export let apiHost;
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
    
    // filter projects
    $: filteredProjects = projects.filter(p => {
        return p.tags.find(t => t == currentTab)
    })

    // replace url
    function replaceUrl(content) {
        let replace = 'src="/'
        let replaceWith = 'src="' + apiHost;
        let reg = new RegExp(replace, "g");
        let newContent = content.replace(reg, replaceWith)
        return newContent;
    }
    // let tae;
    // $: tae = currentTab;

    function changeTab(e) {
        currentTab = e;
    }

    

</script>

<section class="project-wrap">
    <h1>Projects</h1>
    <p>Featured projects I’ve worked with.</p>

    <section class="projects-list">

    {#each filteredProjects as project}

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
            <div class="content">{@html replaceUrl(post.content)}</div>
        </Modal>

    {/if}
</section>

<nav class="project-cat">
    <button class="{currentTab === 'featured' ? 'active' : ''}" on:click="{() => changeTab('featured')}"><i class="icon-all"></i> <span>Featured</span></button>
    <button class="{currentTab === 'typography' ? 'active' : ''}" on:click="{() => changeTab('typography')}"><i class="icon-coffee"></i> <span>Typograhpy</span></button>
    <button class="{currentTab === 'motion' ? 'active' : ''}" on:click="{() => changeTab('motion')}"><i class="icon-motion"></i> <span>Motion</span></button>
    <button class="{currentTab === 'websites' ? 'active' : ''}" on:click="{() => changeTab('websites')}"><i class="icon-webdev"></i> <span>Websites</span></button>
    <button class="{currentTab === 'corporate' ? 'active' : ''}" on:click="{() => changeTab('corporate')}"><i class="icon-suitcase"></i><span>Corporate</span></button>
    <button class="{currentTab === 'others' ? 'active' : ''}" on:click="{() => changeTab('others')}"><i class="icon-others"></i> <span>Others</span></button>
    <button class="{currentTab === 'info' ? 'active' : ''}" on:click="{() => changeTab('info')}"><i class="icon-hand-peace-o"></i> <span>Info</span></button>
</nav>

<style>
    .project-wrap {
        padding: 0 20px 0 75px;
    }


    h1 {
        margin: 0;
    }
    .projects-list {
        display: block;
        margin: 2rem auto 0;
    }
    figure {
        overflow: hidden;
        position: relative;
        margin: 0 0 1.2rem 0;
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

    

    /* media query */
    @media (min-width: 540px) {
        .projects-list {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            grid-gap: 1rem;
        }
        figure {
            margin: 0;
        }
    }

    @media (min-width: 768px) {
        .projects-list {
            grid-template-columns: repeat(3, 1fr);
        }
    }

    @media (min-width: 992px) {
        .project-wrap {
            padding-left: 180px;
        }
        .projects-list {
            grid-template-columns: repeat(4, 1fr);
        }
    }

    @media (min-width: 1600px) {
        
        .projects-list {
            grid-template-columns: repeat(5, 1fr);
        }
    }
</style>