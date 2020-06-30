<script>
	import { Link } from "svelte-routing";
	import NavBar from '../components/NavBar.svelte';
</script>

<header>
    <Link to="/">
        <img class="logo" src="./imgs/logo.svg" alt="Grant Imbo">
    </Link>
	<NavBar/>
</header>
<section>
	<article>
		<h1>About</h1>
		<p>Here's a bit of where I’ve been.</p>

		<p>Hi I'm Grant Imbo, a multimedia designer and front-end Developer.</p>
		
		<h3>2011-2012 : Graphic Designer</h3>
		<ul>
			<li>Creating graphic & motion designs</li>
		</ul>
		
		<h3>2012-2014 : Graphic Designer, WordPress Developer and Front-end Developer</h3>
		<ul>
			<li>Designing graphic related stuff e.i logos, brochure, posters, banners, ebooks and any type of visual expressions.</li>
			<li>Developing WordPress Themes - Converting PSD Mockups to HTML/CSS/JS to WordPress Themes.</li>
			<li>Occationally did some Animations / Explainer Videos</li>
		</ul>
		
		<h3>2014-2016 : Lead Graphic Artist, 3D Designer, Web Developer</h3>
		<ul>
			<li>Rendering 3D Products for Amazon Listings</li>
			<li>Responsible for creating web and graphic related designs.</li>
			<li>Occationally Develop Websites.</li>
		</ul>
		
		<h3>2016-2020 : Jack of all trades. Master of none</h3>
		<ul>
			<li>Working as a one man team in various types of fields.</li>
		</ul>
		
		<p>I believe anything can be overcome through commitment and hard work. Always up for learning new things and never gets satisfied with an average output, always striving for something better and fresh.</p>
		
		<p>Have an idea you'd like to discuss? <br/>
			Shoot a me a message at  <a href="#">grant.imbo@gmail.com</a></p>
		
		<p>Or just want to be friends?  Find me online on most digital platforms <a href="#">@grantimbo</a> or <a href="#">@grntx</a> or by clicking the links below. </p>
		<div class="social-icons">
			<a href="//github.com/grantimbo" target="_blank" alt="Github" rel="noopener"><i class="icon-github"></i></a>
			<a href="//codepen.io/grantimbo" target="_blank" alt="Codepen" rel="noopener"><i class="icon-codepen"></i></a>
			<a href="//instagram.com/grntx" target="_blank" alt="Instagram" rel="noopener"><i class="icon-instagram"></i></a>
			<a href="//facebook.com/grntx" target="_blank" alt="Facebook" rel="noopener"><i class="icon-facebook"></i></a>
			<a href="//artstation.com/grantimbo" target="_blank" alt="Artstation" rel="noopener"><i class="icon-artstation"></i></a>
			<a href="//behance.com/grantimbo" target="_blank" alt="Behance" rel="noopener"><i class="icon-behance"></i></a>
			<a href="//youtube.com/grantimbo" target="_blank" alt="Youtube" rel="noopener"><i class="icon-youtube"></i></a>
		</div>
	</article>
</section>

<style>
	section {
		padding: 1rem;
		max-width: 700px;
		margin: 0 auto;
	}
	article {
		border: 1px solid #1d294a;
		background: #11172e;
		padding: 2rem;
	}
	h1 {
		margin-bottom: 0;
	}
	h1 + p {
		margin-bottom: 2rem;
	}
	
	.social-icons a {
		font-size: 1.4rem;
		margin-right: .8rem;
		text-decoration: none;
	}
	@media (min-width: 620px) { 
		section {
			padding-top: 3rem;
		}
	}
</style>