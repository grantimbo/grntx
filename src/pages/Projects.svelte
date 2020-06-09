<script>
    import Modal from '../components/Modal.svelte';
    import CategoryNavBar from '../components/CategoryNavBar.svelte';
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

<CategoryNavBar/>

<section class="project-wrap">
    <h1>Projects</h1>
    <p>Featured projects I’ve worked with.</p>

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
            <h2 slot="header">{post.title}</h2>
            <p>{post.date}</p>
            <div class="content">{@html replaceUrl(post.content)}</div>
        </Modal>

    {/if}
</section>
