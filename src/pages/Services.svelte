<script>
	import Navbar from '../components/NavBar.svelte';
</script>

<section class="wrap">
	<h2>Services</h2>
	<p>Services I provide</p>

	<section class="service">
		<article>
			<figure></figure>
			<h3>Brand Itentity</h3>
			<p>Logo, poster, banners, ebook or any graphic design needs</p>
			<button>View Samples</button>
			<button>Tools Used</button>
		</article>

		<article>
			<figure></figure>
			<h3>Website & Apps</h3>
			<p>API driven website and apps. We'll use the latest web technologies and frameworks.</p>
			<button>View Samples</button>
			<button>Tools Used</button>
		</article>

		<article>
			<figure></figure>
			<h3>Product Renders</h3>
			<p>Visualize your products in 3D.</p>
			<button>View Samples</button>
			<button>Tools Used</button>
		</article>

		<article>
			<figure></figure>
			<h3>Logo Animation</h3>
			<p>Logo intro reveal animation</p>
			<button>View Samples</button>
			<button>Tools Used</button>
		</article>

		<article>
			<figure></figure>
			<h3>Email Marketing</h3>
			<p>Generate leads</p>
			<button>View Samples</button>
			<button>Tools Used</button>
		</article>
		

	</section>
</section>

<Navbar/>

<style>
	.wrap {
		background: #F2F2F2;
		padding-bottom: 70px;
		text-align: center;
	}
	.wrap > h2 {
		margin: 0;
	}
	.service article {
		background: white;
		padding: 1rem;
		margin-bottom: 1rem;
	}
	.service figure {
		background: #efefef;
		height: 150px;
		width: 100%;
		margin: 0 0 1rem 0;
		padding: 0;
	}
</style>