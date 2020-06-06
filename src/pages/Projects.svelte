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

<nav class="project-cat">
    <Link to="project/featured" ><div><i class="icon-all"></i> <span>Featured</span></div></Link>
    <Link to="project/typography"><div><i class="icon-coffee"></i> <span>Typograhpy</span></div></Link>
    <Link to="project/motion-graphics"><div><i class="icon-motion"></i> <span>Motion</span></div></Link>
    <Link to="project/webdev"><div><i class="icon-webdev"></i> <span>Websites</span></div></Link>
    <Link to="project/corporate"><div><i class="icon-suitcase"></i><span>Corporate</span></div></Link>
    <Link to="project/others"><div><i class="icon-others"></i> <span>Others</span></div></Link>
    <Link to="project/info"><div><i class="icon-hand-peace-o"></i> <span>Info</span></div></Link>
</nav>

<style>
    h1 {
        margin: 0;
    }
    section.projects-wrap {
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
    .details span {
        font-size: 12px;
    }

    /* project-cat nav */
    nav {
        position: fixed;
        background: #000;
        bottom: 0;
        width: 100vw;
        display: grid;
        justify-content: space-evenly;
        grid-template-columns: repeat(7, 1fr);
    }
    nav div {
        color: #fff;
        padding: 1rem;
        display: flex;
        justify-content: center;
    }
    nav span {
        display: none;
    }

    /* media query */
    @media (min-width: 540px) {
        section.projects-wrap {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            grid-gap: 1rem;
        }
        figure {
            margin: 0;
        }
    }

    @media (min-width: 768px) {
        section.projects-wrap {
            grid-template-columns: repeat(3, 1fr);
        }
    }

    @media (min-width: 992px) {
        section.projects-wrap {
            max-width: 1280px;
            grid-template-columns: repeat(4, 1fr);
        }
    }
</style>