<script>
  import { navigate } from "svelte-routing";

  let modal;

  function closeModal(e) {

	if ( e.target.dataset.modal != 'close') {
		return;
	} else {
		window.history.back();
	}
	
  }
</script>


<div class="modal" data-modal="close" role="dialog" on:click={(e) => closeModal(e)} aria-modal="true" bind:this={modal}>
	<div class="modal-container">
		<!-- <div data-modal="close"  on:click={(e) => closeModal(e)}>Close</div> -->
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
		background: #141827bf;
		z-index: 2;
		padding: 1rem;
	}
	.modal-container {
		max-width: 900px;
		background: #090e20;
		border: var(--border);
		margin: 2rem auto;
		min-height: 70vh;
	}
	.content {
		padding: 1rem;
	}


	@media (min-width: 992px) {

	}
</style>
