<script>
	import { Link } from "svelte-routing";
	import Navbar from '../components/NavBar.svelte';
</script>

<header>
    <Link to="/">
        <img class="logo" src="./imgs/logo.svg" alt="Grant Imbo">
    </Link>
    <Navbar/>
</header>
<section class="head">
	<h1>Services</h1>
	<p>Services I offer</p>
</section>
<section class="service">
	<article>
		<img src ="./imgs/services/graphic-design.png" width="240" height="240" alt="Graphic Design">
		<div>
			<h3>Graphic Design</h3>
			<p>Product labels, posters, banners, logos, brochures, ebooks or any visual expressions.</p>
			<button>Examples</button>
		</div>
	</article>

	<article>
		<img src="./imgs/services/website-app.png" width="240" height="240" alt="Websites and Apps">
		<h3>Website & Apps</h3>
		<p>API driven website and apps. We'll use the latest web technologies and frameworks.</p>
		<button>Examples</button>
	</article>

	<article>
		<img src="./imgs/services/product-renders.png" width="240" height="240" alt="Product Renders">
		<h3>Product Renders</h3>
		<p>Visualize your products in 3D.</p>
		<button>Examples</button>
	</article>

	<article>
		<img src="./imgs/services/video-production.png" width="240" height="240" alt="Video Production">
		<h3>Video Production</h3>
		<p>Logo intro reveal animation</p>
		<button>Examples</button>
	</article>

	<article>
		<img src="./imgs/services/email-marketing.png" width="240" height="240" alt="Email Marketing">
		<h3>Email Marketing</h3>
		<p>Generate leads</p>
		<button>Examples</button>
	</article>
	

</section>


<style>
	section.head {
		padding: 3rem 0;
		text-align: center;
	}
	section.head h1,
	section.head p {
		margin: 0;
	}
	section.service {
		padding: 0;
		padding: 1rem;
		text-align: center;
		max-width: 1280px;
		margin: 0 auto;
	}
	article {
		border: 1px solid #1d294a;
		background: #11172e;
		margin-bottom: 1.6rem;
		padding: 2rem;
	}
	article img {
		margin-bottom: 1rem;
	}

	@media (min-width: 620px) {
		section.service {
			display: grid;
			grid-template-columns: 1fr 1fr;
			grid-gap: 2rem;
		}
		article {
			margin: 0;
		}
	}

	@media (min-width: 992px) {
		section.service {
			grid-template-columns: 1fr 1fr 1fr;
		}
	}
	
</style>