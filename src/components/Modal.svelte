<script>
  import { navigate } from "svelte-routing";

  let modal;

  function closeModal() {
    navigate("/projects", { replace: false });
  }
</script>


<div class="modal-background" on:click={() => closeModal()}></div>

<div class="modal" role="dialog" aria-modal="true" bind:this={modal}>
	<slot name="header"></slot>
	<hr>
	<slot></slot>
	<hr>

	<!-- svelte-ignore a11y-autofocus -->
	<button autofocus on:click={() => closeModal()}>close modal</button>
</div>

<style>
	.modal-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0,0,0,0.3);
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
	}

	button {
		display: block;
	}
</style>
