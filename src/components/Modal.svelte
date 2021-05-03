<script>
	import { onMount } from "svelte";
	import { navigate } from "svelte-routing";
	import { projects } from "../_projects";

	export let slug

	let post = {}
	let modal
	let key

	onMount(() => {
		post = projects.find(p => p.slug == slug)
		if (!post) window.location.href = window.location.origin + "/404"
	})

	const handleKeydown = (e) => {
		key = e.key
		if (key == 'ArrowLeft') showPrev()
		if (key == 'ArrowRight') showNext()
		if (key == 'Escape') navigate("/projects", { replace: false })
	}

	const showNext = () => {
		document.querySelector('.modal').scrollTop = 0
		projects.find((p, i) => {
			if (p.slug === slug) {
				let tae = i + 1

				if (tae === projects.length) {
					let gg = projects[0].slug
					post = projects[0]
					navigate(`/projects/${gg}`, { replace: true })
					return
				}
				
				let gg = projects[tae].slug
				post = projects[tae]
				navigate(`/projects/${gg}`, { replace: true })
				
			}
		})
	}

	const showPrev = () => {
		document.querySelector('.modal').scrollTop = 0
		projects.find((p, i) => {
			if (p.slug === slug) {
				let tae = i - 1

				if (tae == -1) {
					let df = projects.length - 1
					let gg = projects[df].slug
					post = projects[df]
					navigate(`/projects/${gg}`, { replace: true })
					return
				}

				let gg = projects[tae].slug
				post = projects[tae]
				navigate(`/projects/${gg}`, { replace: true })
				
			}
		})
	}


	const closeModal = (e) => {
		if ( e.target.dataset.modal != 'close') return
		navigate("/projects", { replace: true })
	}

</script>

<svelte:window on:keydown={handleKeydown}/>

<div class="modal" data-modal="close" role="dialog" aria-modal="true" bind:this={modal} on:click={(e) => closeModal(e)}>
	<div class="modalnav showPrev" on:click={() => showPrev()}><span class="icon-angle-left"></span></div>
	<div class="modalnav showNext" on:click={() => showNext()}><span class="icon-angle-right"></span></div>
	<div class="modal-container">
		<div class="close-modal" on:click={() => navigate("/projects", { replace: true })}><span class="icon-close"></span></div>
		<div class="back"><i class="icon-back-arrow" data-modal="close" on:click={(e) => closeModal(e)}></i> Projects</div>
		<div class="modal-content">
			<div class="header">
				<h3 class="title">{post.title}</h3>
				<p class="date">{post.date}</p>
			</div>
			<div class="content">{@html post.content}</div>
		</div>
	</div>
</div>


<style>
	.modal {
		position: fixed;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		overflow: auto;
		background: #090e20;
		z-index: 2;
		cursor: context-menu;
	}
	.modalnav {
		position: fixed;
		top: 400px;
		width: 50px;
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 2.5rem;
		z-index: 1;
		background: #1d294a96;
		border-radius: 2px;
		color: #ffffff;
		height: 47px;
	}
	.modalnav span {
		padding-bottom: 3px;
	}
	.modalnav:hover span {
		color: #3366be;
	}
	.showPrev {
		left: 0;
	}
	.showNext {
		right: 0;
	}
	.modal-container {
		background: #090e20;
		min-height: 60vh;
	}
	.close-modal {
		display: none;
	}
	.back {
		background: #11172e;
		border-bottom: 1px solid #1d294a;
		color: white;
		padding: 1rem;
		font-size: 1.2rem;
		display: flex;
		align-items: center;
	}
	.back i {
		margin-right: 10px;
		cursor: pointer;
	}
	.modal-content {
		padding: 1rem;
	}
	h3.title {
		font-size: 1.3rem;
		margin-bottom: 0.2rem;
	}
	p.date {
		font-size: .8rem;
		margin-bottom: 1rem;
	}


	@media (min-width: 768px) {
		.close-modal {
			position: absolute;
			cursor: pointer;
			top: 1.3rem;
			right: 1.2rem;
			font-size: 2rem;
			background: #1d294a;
			color: #4072cc;
			width: 3rem;
			height: 3rem;
			display: flex;
			align-items: center;
			border-radius: 2px;
			justify-content: center;
		}
		.close-modal:hover {
			color: #fff;
		}
		.back {
			display: none;
		}
		.modal {
			background: #141827bf;
		}
		.modal-container {
			position:relative;
			max-width: 720px;
			background: #090e20;
			border: var(--border);
			margin: 3rem auto;
		}
	}
	@media (min-width: 992px) {
		.modal-container {
			max-width: 900px;
		}
	}
	@media (min-width: 1200px) {
		.modal-container {
			max-width: 1000px;
		}
		.modalnav {
			top: 0;
			width: 160px;
			cursor: pointer;
			display: flex;
			align-items: center;
			justify-content: center;
			font-size: 3.5rem;
			border: 0;
			height: 100%;
		}
		.modalnav:hover span {
			color: #fff;
		}
		.modalnav span {
			background: #1d294a;
			color: #4072cc;
			border-radius: 2px;
			padding: 0 20px 4px;
		}
		.showPrev {
			background: linear-gradient(90deg, #00061b, #ffffff00);
		}
		.showNext {
			background: linear-gradient(90deg, #ffffff00, #00061b);
		}
	}
</style>
