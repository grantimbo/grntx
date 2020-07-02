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
	<img srcset="./imgs/services-head-sm.png 560w,
				./imgs/services-head-lg.png 1066w"
		sizes="(max-width: 768px) 560px, 1066px"
		src="./imgs/services-head-lg.png"
		width="1066"
		height="574"
		alt="Email Marketing">
</section>
<section class="service">
	<article>
		<div class="flex img">
			<img srcset="./imgs/services/graphic-design-sm.png 150w,
						./imgs/services/graphic-design-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="./imgs/services/graphic-design-lg.png"
				width="323"
				height="323"
				alt="Graphic Design">
		</div>
		<div class="flex">
			<div>
				<h3>Graphic Design</h3>
				<p>Product labels, posters, banners, logos, brochures, ebooks or any visual expressions.</p>
				<button>Examples</button>
			</div>
		</div>
	</article>

	<article>
		<div class="flex">
			<div>
				<h3>Website & Apps</h3>
				<p>API driven website and apps using the latest technologies and frameworks such as Svelte, Flutter, etc.</p>
				<button>Examples</button>
			</div>
		</div>
		<div class="flex img">
			<img srcset="./imgs/services/website-apps-sm.png 150w,
						./imgs/services/website-apps-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="./imgs/services/website-apps-lg.png"
				width="323"
				height="323"
				alt="Websites and Apps">
		</div>
	</article>

	<article>
		<div class="flex img">
			<img srcset="./imgs/services/product-renders-sm.png 150w,
						./imgs/services/product-renders-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="./imgs/services/product-renders-lg.png"
				width="323"
				height="323"
				alt="Product Renders">
		</div>
		<div class="flex">
			<div>
				<h3>Product Renders</h3>
				<p>High quality 3D realistic renderings of products that will surely increase your sales on Amazon.</p>
				<button>Examples</button>
			</div>
		</div>
	</article>

	<article>
		<div class="flex">
			<div>
				<h3>Video Production</h3>
				<p>Logo intro reveal, Explainer videos, Motion design in 2D/3D or a simple VFX animation.</p>
				<button>Examples</button>
			</div>
		</div>
		<div class="flex img">
			<img srcset="./imgs/services/video-production-sm.png 150w,
						./imgs/services/video-production-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="./imgs/services/video-production-lg.png"
				width="323"
				height="323"
				alt="Video Production">
		</div>
	</article>

	<article>
		<div class="flex img">
			<img srcset="./imgs/services/email-marketing-sm.png 150w,
						./imgs/services/email-marketing-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="./imgs/services/email-marketing-lg.png"
				width="323"
				height="323"
				alt="Email Marketing">
		</div>
		<div class="flex">
			<div>
				<h3>Email Marketing</h3>
				<p>Generate leads, Run a webinar, Sell your products. We'll use tools like Clickfunnels, AWeber and more.</p>
				<button>Examples</button>
			</div>
		</div>
	</article>
	

</section>


<style>
	section.head {
		text-align: center;
	}
	section.service {
		padding: 0;
		padding: 1rem;
		margin: 0 auto;
	}
	article {
		display: grid;
		grid-template-columns: 1fr 1.5fr;
		grid-gap: 1rem;
		margin-bottom: 4rem;
	}
	article:nth-child(even) {
		grid-template-columns: 1.5fr 1fr;
		text-align: right;
	}
	article .flex {
		display:flex;
		align-items: center;
	}
	article .flex.img {
		justify-content: center;
	}
	article h3 {
		color: var(--eggblue);
	}

	@media (min-width: 768px) {
		section.service {
			max-width: 900px;
			margin: 0 auto;
		}
	}
	
</style>