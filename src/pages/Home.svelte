<script>
    import { Link } from "svelte-routing";
</script>

<section>
    <article class="home">
        <h1>Hello. I'm Grant</h1>
        <p>I'm a multimedia artist creating cool stuff across the web and a developer focusing mainly on front-end.</p>
        <Link to="/projects">All Projects</Link>
        <Link to="/project-type/featured">Featured</Link>
    </article>
</section>

<style>
    section {
        height: 100vh;
        display: flex;
        align-items: center;
    }
    article {
        max-width: 500px;
        text-align: center;
        margin: 0 auto;
    }
    p {
        margin-bottom: 1rem;
    }
</style>