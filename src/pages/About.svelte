<script>
	import NavBar from '../components/NavBar.svelte';
	import { Link } from "svelte-routing";
	import { fly } from 'svelte/transition';
</script>

<header>
    <Link to="/">
        <img class="logo" src="/imgs/logo.svg" alt="Grant Imbo">
    </Link>
	<NavBar/>
</header>
<section class="head">
	<img in:fly={{y: 20, duration: 1000}} srcset="/imgs/about-head-sm.png 560w,
				/imgs/about-head-lg.png 1066w"
		sizes="(max-width: 768px) 150px, 1066px"
		src="/imgs/about-head-lg.png"
		width="1066"
		height="574"
		alt="About">
</section>
<section class="about">
	<article>
		<h2 in:fly={{y: 20, duration: 1000, delay:300}}>Here's a bit of where I’ve been.</h2>
		
		<h3 in:fly={{y: 20, duration: 1000, delay:400}}>2011-2012 : Graphic / Motion Designer</h3>
		<ul in:fly={{y: 20, duration: 1000, delay:400}}>
			<li>Creating graphic & motion designs.</li>
		</ul>
		
		<h3 in:fly={{y: 20, duration: 1000, delay:600}}>2012-2014 : Graphic Designer, WordPress Developer and Front-end Developer</h3>
		<ul in:fly={{y: 20, duration: 1000, delay:600}}>
			<li>Designing graphic related stuff e.i logos, brochure, posters, banners, ebooks or any type of visual expressions.</li>
			<li>Developing WordPress themes - designing PSD mockups, converting them to HTML/CSS/JS then to WordPress themes.</li>
			<li>Occationally did some animations / explainer videos.</li>
		</ul>
		
		<h3 in:fly={{y: 20, duration: 1000, delay:800}}>2014-2016 : Lead Graphic Designer, 3D Artist, Web Developer</h3>
		<ul in:fly={{y: 20, duration: 1000, delay:800}}>
			<li>Rendering high quality 3D products for Amazon listings.</li>
			<li>Responsible for creating web and graphic related designs.</li>
			<li>Occationally develop websites.</li>
		</ul>
		
		<h3 in:fly={{y: 20, duration: 1000, delay:1000}}>2016-2020 : Full Stack Developer, Designer</h3>
		<ul in:fly={{y: 20, duration: 1000, delay:1000}}>
			<li>Building websites.</li>
			<li>Designing graphics for the web.</li>
		</ul>
		
		<p in:fly={{y: 20, duration: 1000, delay:1200}}>I believe anything can be overcome through commitment and hard work. Always up for learning new things and never gets satisfied with an average output, always striving for something better and fresh.</p>
		
		<p in:fly={{y: 20, duration: 1000, delay:1300}}>Have an idea you'd like to discuss? <br/>
			Feel free to contact me at  <span>grant.imbo@gmail.com</span></p>
		
		<p in:fly={{y: 20, duration: 1000, delay:1400}}>Or just want to be friends?  Find me online on most digital platforms <span>@grantimbo</span> or <span>@grntx</span> or by clicking the links below. </p>
		<div class="social-icons" in:fly={{y: 20, duration: 1000, delay:300}}>
			<a href="https://youtube.com/grantimbo" target="_blank" alt="Youtube" rel="noopener"><i class="icon-youtube"></i></a>
			<a href="https://facebook.com/grntx" target="_blank" alt="Facebook" rel="noopener"><i class="icon-facebook"></i></a>
			<a href="https://instagram.com/grntx" target="_blank" alt="Instagram" rel="noopener"><i class="icon-instagram"></i></a>
			<a href="https://twitter.com/grantimbo" target="_blank" alt="Twitter" rel="noopener"><i class="icon-twitter"></i></a>
			<a href="https://github.com/grantimbo" target="_blank" alt="Github" rel="noopener"><i class="icon-github"></i></a>
			<a href="https://codepen.io/grantimbo" target="_blank" alt="Codepen" rel="noopener"><i class="icon-codepen"></i></a>
			<a href="https://artstation.com/grantimbo" target="_blank" alt="Artstation" rel="noopener"><i class="icon-artstation"></i></a>
			<a href="https://behance.net/grantimbo" target="_blank" alt="Behance" rel="noopener"><i class="icon-behance"></i></a>
		</div>
	</article>
</section>

<style>
	section.head {
		text-align: center;
	}
	section.about {
		max-width: 620px;
		margin: 0 auto;
	}
	article {
		padding: 1rem;
	}
	h2 {
		margin-bottom: 1.5rem;
		color: var(--eggblue);
	}
	ul {
		padding-left: 2.2rem;
		margin-bottom: 1.2rem;
	}
	span {
		color: var(--eggblue);
	}
	.social-icons {
		margin: 2rem 0;
	}
	.social-icons a {
		font-size: 1.4rem;
		margin-right: .8rem;
		text-decoration: none;
		color: var(--eggblue);
	}
</style>