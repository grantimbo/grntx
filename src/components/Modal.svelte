<script>
  import { navigate } from "svelte-routing";

  let modal;

  function closeModal() {
	window.history.back();
  }
</script>


<div class="modal" role="dialog" aria-modal="true" bind:this={modal}>
	<div class="back"><i class="icon-back-arrow" on:click={() => closeModal()}></i> Projects</div>
	<div class="content">
		<slot name="header"></slot>
		<slot name="content"></slot>
	</div>
</div>

<div class="modal-background" on:click={() => closeModal()}></div>

<style>
	.modal-background {
		display: none;
	}
	.modal {
		position: fixed;
		top: 0;
		bottom: 0;
		left: 0;
		right: 0;
		overflow: auto;
		background: #090e20;
		z-index: 2;
		padding-bottom: 60px;
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


	@media (min-width: 992px) {
		.modal-background {
			position: fixed;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			background: rgba(0, 0, 0, 0.397);
			z-index: 3;
		}
	}
</style>
