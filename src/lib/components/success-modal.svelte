<script lang="ts">
	export let closeModal: () => void;
</script>

<div class="success-modal">
	<div class="modal">
		<img src="./icon-success.svg" alt="icon-img" />
		<h2>Thanks for subscribing!</h2>

		<p>
			A confirmation email has been sent to{' '}
			<span>ash@loremcompany.com.</span> Please open it and click the button inside to confirm your subscription.
		</p>

		<button class="dismiss-btn" on:click={closeModal}> Dismiss message </button>
	</div>
</div>

<style>
	.success-modal {
		position: fixed;
		height: 100%;
		width: 100%;
		top: 0;
		left: 0;
		z-index: 3;
		background-color: hsl(0, 0%, 100%);
		color: hsl(234, 29%, 20%);
		padding: 5rem 2rem 0;
	}

	.success-modal img {
		width: 3.5rem;
		height: 3.5rem;
		margin-bottom: 2rem;
	}

	h2 {
		font-size: 2rem;
		padding-bottom: 2rem;
		line-height: 1;
	}

	span {
		font-weight: 600;
	}

	p {
		line-height: 1.5;
	}

	.dismiss-btn {
		margin-top: 10rem;
	}

	@media screen and (min-width: 800px) {
		.success-modal {
            background-color: hsl(235, 18%, 26%);
            padding: 0;
		}

		.modal {
            position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
            border-radius: 20px;
			padding: 3rem;
			max-width: 420px;
            background-color: hsl(0, 0%, 100%);
		}

		.dismiss-btn {
			margin-top: 2rem;
		}

		h2 {
			font-size: 2.5rem;
		}

		.success-modal img {
			width: 3rem;
			height: 3rem;
		}
	}
</style>
