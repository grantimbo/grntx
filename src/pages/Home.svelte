<script>
    import { Link } from "svelte-routing";
    import Navbar from '../components/NavBar.svelte';
</script>

<header>
    <img src="./imgs/logo.png" alt="Grant Imbo">
</header>
<section>
    <article>
        <h1>Artist. Developer. Animator</h1>
        <p>Hello I'm Grant, a multimedia designer creating cool stuff across the web and a developer focusing mainly on front-end.</p>
    </article>
</section>

<Navbar/>

<style>
    header {
        padding: 1rem;
    }
    header img {
        max-width: 50px;
    }
    section {
        height: 100vh;
        display: flex;
        align-items: center;
    }
    article {
        max-width: 500px;
        text-align: center;
        margin: 0 auto;
        padding: 1rem;
    }
    h1 {
        font-size: 1.3rem;
        font-weight: bold;
    }
    p {
        margin-bottom: 1rem;
    }
</style>