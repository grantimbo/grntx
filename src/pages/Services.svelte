<script>
	import Navbar from '../components/NavBar.svelte';
	import { Link } from "svelte-routing";
	import { fly } from 'svelte/transition';
</script>

<header>
    <Link to="/">
        <img class="logo" src="/imgs/logo.svg" alt="Grant Imbo">
    </Link>
    <Navbar/>
</header>
<section in:fly={{y: 20, duration: 1000}} class="head">
	<img srcset="/imgs/services-head-sm.png 560w,
				/imgs/services-head-lg.png 1066w"
		sizes="(max-width: 768px) 560px, 1066px"
		src="/imgs/services-head-lg.png"
		width="1066"
		height="574"
		alt="Email Marketing">
</section>
<section class="service">
	<article>
		<div in:fly={{y: 20, duration: 1000, delay:300}} class="flex img">
			<img srcset="/imgs/services/graphic-design-sm.png 150w,
						/imgs/services/graphic-design-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="/imgs/services/graphic-design-lg.png"
				width="323"
				height="323"
				alt="Graphic Design">
		</div>
		<div class="flex">
			<div>
				<h3 in:fly={{y: 20, duration: 1000, delay:400}}>Graphic Design</h3>
				<p in:fly={{y: 20, duration: 1000, delay:500}}>Product labels, posters, banners, logos, brochures, ebooks or any visual expressions.</p>
			</div>
		</div>
	</article>

	<article>
		<div class="flex">
			<div>
				<h3 in:fly={{y: 20, duration: 1000, delay:900}}>Website & Apps</h3>
				<p in:fly={{y: 20, duration: 1000, delay:1000}}>API driven websites and apps using the latest technologies and frameworks.</p>
			</div>
		</div>
		<div in:fly={{y: 20, duration: 1000, delay:800}} class="flex img">
			<img srcset="/imgs/services/website-apps-sm.png 150w,
						/imgs/services/website-apps-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="/imgs/services/website-apps-lg.png"
				width="323"
				height="323"
				alt="Websites and Apps">
		</div>
	</article>

	<article>
		<div in:fly={{y: 20, duration: 1000, delay:1300}} class="flex img">
			<img srcset="/imgs/services/product-renders-sm.png 150w,
						/imgs/services/product-renders-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="/imgs/services/product-renders-lg.png"
				width="323"
				height="323"
				alt="Product Renders">
		</div>
		<div class="flex">
			<div>
				<h3 in:fly={{y: 20, duration: 1000, delay:1400}}>Product Renders</h3>
				<p in:fly={{y: 20, duration: 1000, delay:1500}}>High quality realistic product 3D renderings that will increase your sales on Amazon.</p>
			</div>
		</div>
	</article>

	<article>
		<div class="flex">
			<div>
				<h3 in:fly={{y: 20, duration: 1000, delay:1900}}>Video Production</h3>
				<p in:fly={{y: 20, duration: 1000, delay:2000}}>Logo intro reveal, Explainer videos, Motion design in 2D/3D or a simple VFX animation.</p>
			</div>
		</div>
		<div in:fly={{y: 20, duration: 1000, delay:1800}} class="flex img">
			<img srcset="/imgs/services/video-production-sm.png 150w,
						/imgs/services/video-production-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="/imgs/services/video-production-lg.png"
				width="323"
				height="323"
				alt="Video Production">
		</div>
	</article>

	<article>
		<div in:fly={{y: 20, duration: 1000, delay:2300}} class="flex img">
			<img srcset="/imgs/services/email-marketing-sm.png 150w,
						/imgs/services/email-marketing-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="/imgs/services/email-marketing-lg.png"
				width="323"
				height="323"
				alt="Email Marketing">
		</div>
		<div class="flex">
			<div>
				<h3 in:fly={{y: 20, duration: 1000, delay:2400}}>Marketing</h3>
				<p in:fly={{y: 20, duration: 1000, delay:2500}}>Generate leads, Run a webinar, Sell your products and leverage the power of social media marketing.</p>
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