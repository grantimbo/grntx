<script>
	import ModalService from '../components/ModalService.svelte';
	import Navbar from '../components/NavBar.svelte';
	import { services } from "../_services";
	import { Link } from "svelte-routing";

	export let slug;

    let showModal = false;
    let post;
    
    // if single post
    if (slug) {
        showModal = true;
        post = services.find(p => p.slug == slug);

        if (!post) {
            window.location.href = window.location.origin + "/404";
        }
	}
	
</script>

<header>
    <Link to="/">
        <img class="logo" src="/imgs/logo.svg" alt="Grant Imbo">
    </Link>
    <Navbar/>
</header>
<section class="head">
	<img srcset="https://assets.grantimbo.com/imgs/services-head-sm.png 560w,
				https://assets.grantimbo.com/imgs/services-head-lg.png 1066w"
		sizes="(max-width: 768px) 560px, 1066px"
		src="https://assets.grantimbo.com/imgs/services-head-lg.png"
		width="1066"
		height="574"
		alt="Email Marketing">
</section>
<section class="service">
	<article>
		<div class="flex img">
			<img srcset="https://assets.grantimbo.com/imgs/services/graphic-design-sm.png 150w,
						https://assets.grantimbo.com/imgs/services/graphic-design-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="https://assets.grantimbo.com/imgs/services/graphic-design-lg.png"
				width="323"
				height="323"
				alt="Graphic Design">
		</div>
		<div class="flex">
			<div>
				<h3>Graphic Design</h3>
				<p>Product labels, posters, banners, logos, brochures, ebooks or any visual expressions.</p>
			</div>
		</div>
	</article>

	<article>
		<div class="flex">
			<div>
				<h3>Website & Apps</h3>
				<p>API driven websites and apps using the latest technologies and frameworks such as Svelte, Flutter, etc.</p>
			</div>
		</div>
		<div class="flex img">
			<img srcset="https://assets.grantimbo.com/imgs/services/website-apps-sm.png 150w,
						https://assets.grantimbo.com/imgs/services/website-apps-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="https://assets.grantimbo.com/imgs/services/website-apps-lg.png"
				width="323"
				height="323"
				alt="Websites and Apps">
		</div>
	</article>

	<article>
		<div class="flex img">
			<img srcset="https://assets.grantimbo.com/imgs/services/product-renders-sm.png 150w,
						https://assets.grantimbo.com/imgs/services/product-renders-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="https://assets.grantimbo.com/imgs/services/product-renders-lg.png"
				width="323"
				height="323"
				alt="Product Renders">
		</div>
		<div class="flex">
			<div>
				<h3>Product Renders</h3>
				<p>High quality 3D realistic product renderings that will increase your sales on Amazon.</p>
			</div>
		</div>
	</article>

	<article>
		<div class="flex">
			<div>
				<h3>Video Production</h3>
				<p>Logo intro reveal, Explainer videos, Motion design in 2D/3D or a simple VFX animation.</p>
			</div>
		</div>
		<div class="flex img">
			<img srcset="https://assets.grantimbo.com/imgs/services/video-production-sm.png 150w,
						https://assets.grantimbo.com/imgs/services/video-production-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="https://assets.grantimbo.com/imgs/services/video-production-lg.png"
				width="323"
				height="323"
				alt="Video Production">
		</div>
	</article>

	<article>
		<div class="flex img">
			<img srcset="https://assets.grantimbo.com/imgs/services/email-marketing-sm.png 150w,
						https://assets.grantimbo.com/imgs/services/email-marketing-lg.png 323w"
				sizes="(max-width: 768px) 150px, 323px"
				src="https://assets.grantimbo.com/imgs/services/email-marketing-lg.png"
				width="323"
				height="323"
				alt="Email Marketing">
		</div>
		<div class="flex">
			<div>
				<h3>Marketing</h3>
				<p>Generate leads, Run a webinar, Sell your products and leverage the power of social media marketing.</p>
			</div>
		</div>
	</article>
	

</section>

{#if post}

	<ModalService on:close="{() => showModal = false}">
		<div slot="header">
			<h3>{post.title}</h3>
		</div>
		<div slot="content">{@html post.content}</div>
	</ModalService>

{/if}


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