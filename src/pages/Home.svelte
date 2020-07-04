<script>
    import { Link } from "svelte-routing";
    import Navbar from '../components/NavBar.svelte';
</script>

<header>
    <Link to="/">
        <img class="logo" src="/imgs/logo.svg" alt="Grant Imbo">
    </Link>
    <Navbar/>
</header>
<section class="contents">
    <figure>
        <img srcset="/imgs/home-bg-sm.png 640w,
                    /imgs/home-bg-lg.png 1104w"
            sizes="(max-width: 768px) 640px, 1104px"
            src="/imgs/home-bg-lg.png"
            width="1104"
            height="930"
            alt="Creator Thinker">
    </figure>
    <section>
        <article>
            <h2>Hello I'm Grant.</h2>
            <p>I'm a multimedia designer creating cool stuff across the web and a developer focusing mainly on <span style="white-space: nowrap;">front-end.</span></p>
        </article>
    </section>
</section>



<style>
    
    figure {
        padding: 0;
        margin: 0;
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
    p {
        margin-bottom: 1rem;
    }

    @media (min-width: 768px) {
        
        .contents {
            display: grid;
            grid-template-columns: 1.6fr 1fr;
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

    
</style>