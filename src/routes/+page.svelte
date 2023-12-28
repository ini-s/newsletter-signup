<script lang="ts">
	import './global.css';

	import validator from 'validator';

	import SuccessModal from '$lib/components/success-modal.svelte';

	let errorMessage = false;
	let showSuccessMessage = false;
	let email = '';

	const errorStyle = `
		border: errorMessage ? '1.5px solid hsl(4, 100%, 67%)' : '1.5px solid hsl(231, 7%, 60%)',
		color: errorMessage ? 'hsl(4, 100%, 67%)' : 'black',
		backgroundColor: errorMessage ? 'hsl(2, 100%, 90%)' : 'hsl(0, 0%, 100%)'
	`;

	function validateEmail() {
		validator.isEmail(email) ? (errorMessage = false) : (errorMessage = true);
	}

	function openModal() {
		if (email !== '' && !errorMessage) {
			showSuccessMessage = true;
		}
	}

	function closeModal() {
		showSuccessMessage = false;
		email = '';
	}
</script>

<main>
	<div class="container">
		<div class="image-box">
			<img
				class="illustration-mobile-img"
				src="./illustration-sign-up-mobile.svg"
				alt="illustration-mobile"
			/>
			<img
				class="illustration-desktop-img"
				src="./illustration-sign-up-desktop.svg"
				alt="illustration-desktop"
			/>
		</div>
		<div class="text-container">
			<h1>Stay updated!</h1>
			<p>Join 60,000+ product managers receiving monthly updates on:</p>
			<ul>
				<li>
					<img class="list-icon-img" src="./list-icon.svg" alt="list-icon-img" />
					<p>Product discovery and building what matters</p>
				</li>
				<li>
					<img class="list-icon-img" src="./list-icon.svg" alt="list-icon-img" />
					<p>Measuring to ensure updates are a success</p>
				</li>
				<li>
					<img class="list-icon-img" src="./list-icon.svg" alt="list-icon-img" />
					<p>And much more!</p>
				</li>
			</ul>
			<div class="form">
				<div class="email-flexbox">
					<p class="email">Email address</p>
					{#if errorMessage}
						<p class="error-msg">Valid Email required</p>
					{/if}
				</div>
				<input
					on:change={validateEmail}
					type="email"
					placeholder="email@company.com"
					bind:value={email}
					style={errorStyle}
				/>
				<button on:click={openModal}>Subscribe to monthly newsletter</button>
			</div>
		</div>
	</div>
	{#if showSuccessMessage}
		<SuccessModal {closeModal} />
	{/if}
</main>

<style>
	ul {
		list-style: none;
		margin-bottom: 1.5rem;
	}

	.illustration-mobile-img,
	.illustration-desktop-img {
		width: 100%;
	}

	.illustration-desktop-img {
		display: none;
	}

	.text-container {
		padding: 2rem 1rem;
	}

	h1 {
		padding-bottom: 1.5rem;
		color: hsl(234, 29%, 20%);
	}

	.text-container > p {
		padding-bottom: 1.5rem;
	}

	li {
		padding-bottom: 1rem;
		display: flex;
		align-items: start;
		gap: 0.7rem;
	}

	.email-flexbox {
		display: flex;
		justify-content: space-between;
	}

	.email,
	.error-msg {
		padding-bottom: 0.5rem;
		font-weight: 600;
		font-size: 13px;
	}

	.email {
		color: hsl(234, 29%, 20%);
	}

	.error-msg {
		color: hsl(4, 100%, 67%);
	}

	input {
		padding: 1rem;
		margin-bottom: 1.5rem;
		border: 1px solid hsl(231, 7%, 60%);
	}

	input:focus {
		outline: none;
	}

	input:hover {
		border-color: black;
	}

	p {
		line-height: 1.5;
	}

	@media screen and (min-width: 50em) {
		.container {
			display: flex;
			flex-direction: row-reverse;
			align-items: center;
			background-color: hsl(0, 0%, 100%);
			padding: 5rem;
			border-radius: 20px;
			width: 90%;
			max-width: 900px;
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
		}

		.illustration-desktop-img {
			display: block;
		}

		.illustration-mobile-img {
			display: none;
		}

		.text-container {
			padding: 0 3.5rem 0 2rem;
			flex-basis: 60%;
		}

		.image-box {
			flex-basis: 40%;
		}
	}

	@media screen and (min-width: 50em) {
		main {
			padding: 1.5rem;
		}
	}
</style>
