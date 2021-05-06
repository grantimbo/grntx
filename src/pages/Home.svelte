<script>
    import { Link } from "svelte-routing";
    import { fly } from 'svelte/transition';
    import Navbar from '../components/NavBar.svelte';
</script>

<header>
    <Link to="/">
        <img class="logo" src="/imgs/logo.svg" alt="Grant Imbo">
    </Link>
    <Navbar/>
</header>
<section class="contents">
    <figure in:fly={{y: 20, duration: 1000}}>
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
            <h2 in:fly={{y: 20, duration: 1000, delay:300}}>Hi. I'm Grant.</h2>
            <p in:fly={{y: 20, duration: 1000, delay:500}}>Developer by day.. Artist by night.. Curently working as a full-time JavaScript Developer and making <a href="https://youtube.com/grantimbo" target="_blank">3D videos</a> on YouTube for fun.</p>
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