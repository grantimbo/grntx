<script>
    import { Link } from "svelte-routing";
    import Navbar from '../components/NavBar.svelte';
</script>

<div class="wrap">
    <header>
        <img src="./imgs/logo.png" alt="Grant Imbo">
    </header>
    <section>
        <figure>
        </figure>
        <article>
            <h1>Artist. Developer. Animator</h1>
            <p>Hello I'm Grant, a multimedia designer creating cool stuff across the web and a developer focusing mainly on front-end.</p>
        </article>
    </section>
</div>

<Navbar/>

<style>
    header {
        margin-bottom: 2rem;
    }
    header img {
        max-width: 40px;
        margin: 0 auto;
    }
    figure {
        background: #f3f3f3;
        height: 50vh;
        display: block;
        margin: 0 0 2rem 0;
    }
    article {      
        text-align: center;
    }
    h1 {
        font-size: 1.3rem;
    }
    p {
        margin-bottom: 1rem;
    }
</style>