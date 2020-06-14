<script>
  import { navigate } from "svelte-routing";

  let modal;

  function closeModal() {
	window.history.back();
  }
</script>


<div class="modal" role="dialog" aria-modal="true" bind:this={modal}>
	<div class="back"><i class="material-icons" on:click={() => closeModal()}>keyboard_backspace</i> Projects</div>
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
		background: #fff;
		color: #000;
		z-index: 2;
		padding-bottom: 60px;
	}
	.back {
		background: black;
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

	/* .modal-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0,0,0,0.3);
		z-index: 3;
	}

	.modal {
		position: absolute;
		left: 50%;
		top: 50%;
		width: calc(100vw - 4em);
		max-width: 1400px;
		max-height: calc(100vh - 4em);
		overflow: auto;
		transform: translate(-50%,-50%);
		padding: 1em;
		background: #fff;
		color: #000;
		z-index: 4;
	}

	i {
		position: absolute;
		top: .5rem;
		right: .5rem;
	} */
</style>
