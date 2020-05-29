<script>
    import { Link } from "svelte-routing";
</script>

<section>
    <div>
        <h1>404 Not Found</h1>
        <p>Seems like you're lost. Please Go back <Link to="/">Home</Link></p>
    </div>
</section>

<style>
    section {
        display:flex;
        align-items: center;
        height: 100vh;
        text-align: center;
    }
    h1 {
        margin: 0;
    }
    div {
        max-width: 500px;
        margin: 0 auto;
    }
</style>