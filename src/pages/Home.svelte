<script>
    import { Link } from "svelte-routing";
    import Navbar from '../components/NavBar.svelte';
</script>

<header>
    <img class="logo" src="./imgs/logo.png" alt="Grant Imbo">
    <Navbar/>
</header>
<section class="contents">
    <figure>
        <img srcset="./imgs/home-bg-sm.jpg 600w, ./imgs/home-bg-lg.jpg 1280w" src="./imgs/home-bg-lg.jpg" width="1104" height="930" alt="Creator. Thinker">
    </figure>
    <section>
        <article>
            <h1>Hello I'm Grant.</h1>
            <p>I'm a multimedia designer creating cool stuff across the web and a developer focusing mainly on <span style="white-space: nowrap;">front-end.</span></p>
        </article>
    </section>
</section>



<style>
    .logo {
        display: none;
        max-width: 40px;
        margin: 0 auto;
    }
    figure {
        padding: 0;
        margin: 0;
        height: 60vh;
        display: flex;
        align-items: center;
    }
    figure img {
        background: #090e20
    }
    .contents article {
        max-width: 450px;
        text-align: center;
        padding: 1.3rem;
        margin: 0 auto;
    }
    h1 {
        font-size: 1.3rem;
    }
    p {
        margin-bottom: 1rem;
    }

    @media (min-width: 768px) {
        header {
            display: grid;
            grid-template-columns: 1fr 2fr;
        }
        .logo {
            display: inline-block;
        }
        .contents {
            display: grid;
            grid-template-columns: 2fr 1fr;
            max-width: 1600px;
            margin: 0 auto;
        }
        .contents section {
            display: flex;
            align-items: center;
        }
        .contents article {
            text-align: left;
            margin: 0;
        }
    }

    @media (min-width: 1280px) {
        h1 {
            font-size: 1.6rem;
        }
        p {
            font-size: 1.1rem;
        }
    }
</style>