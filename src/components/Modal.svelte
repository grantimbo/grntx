<script>
  import { navigate } from "svelte-routing";

  let modal;

  function closeModal(e) {
	if ( e.target.dataset.modal != 'close') {
		return;
	} else {
		navigate("/projects", { replace: false });
	}
  }
</script>


<div class="modal" data-modal="close" role="dialog" aria-modal="true" bind:this={modal} on:click={(e) => closeModal(e)}>
	<div class="modal-container">
		<div class="back"><i class="icon-back-arrow" data-modal="close" on:click={(e) => closeModal(e)}></i> Projects</div>
		<div class="content">
			<slot name="header"></slot>
			<slot name="content"></slot>
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
	}
	.modal-container {
		background: #090e20;
		min-height: 80vh;
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
	.content {
		padding: 1rem;
	}


	@media (min-width: 768px) {
		.back {
			display: none;
		}
		.modal {
			background: #141827bf;
		}
		.modal-container {
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
	}
</style>
