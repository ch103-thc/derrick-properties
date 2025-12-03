<script>
	import Icon from '@iconify/svelte';

	let formData = $state({
		name: '',
		email: '',
		phone: '',
		subject: '',
		referral: '',
		referralOther: '',
		message: '',
		consent: false
	});

	let formStatus = $state('');

	async function handleSubmit(e) {
		e.preventDefault();
		formStatus = 'loading';

		try {
			// Replace with your Google Apps Script Web App URL
			const response = await fetch(
				'https://script.google.com/macros/s/AKfycbwYkfARtsAmv_uQljE-uZ649fOF8v0FPYj5KZISzSK0Dh8i5QBYw9hTMinELUKJOyKU/exec',
				{
					method: 'POST',
					mode: 'no-cors',
					headers: {
						'Content-Type': 'application/json'
					},
					body: JSON.stringify(formData)
				}
			);

			formStatus = 'success';
			console.log('Form submitted:', formData);

			// Reset form after 3 seconds
			setTimeout(() => {
				formData = { name: '', email: '', phone: '', subject: '', message: '', consent: false };
				formStatus = '';
			}, 3000);
		} catch (error) {
			formStatus = 'error';
			console.error('Error submitting form:', error);
		}
	}
</script>

<section class="contact-hero">
	<div class="container">
		<h1 class="hero-title">Get In Touch</h1>
		<p class="hero-subtitle">
			Ready to make your next move? Let's discuss how I can help you achieve your real estate goals.
		</p>
	</div>
</section>

<section class="contact-section">
	<div class="container">
		<div class="contact-grid">
			<!-- Contact Information -->
			<div class="contact-info">
				<h2>Let's Connect</h2>
				<p class="intro-text">
					Whether you're looking to upgrade your portfolio, explore new investment opportunities, or
					need expert guidance on your property journey, I'm here to help.
				</p>

				<div class="info-cards">
					<div class="info-card">
						<div class="icon-wrapper">
							<Icon icon="mdi:phone" width="24" height="24" />
						</div>
						<div class="info-text">
							<h3>Phone</h3>
							<a href="tel:+6512345678">+65 1234 5678</a>
						</div>
					</div>

					<div class="info-card">
						<div class="icon-wrapper">
							<Icon icon="mdi:email" width="24" height="24" />
						</div>
						<div class="info-text">
							<h3>Email</h3>
							<a href="mailto:info@yourdomain.com">info@yourdomain.com</a>
						</div>
					</div>

					<div class="info-card">
						<div class="icon-wrapper">
							<Icon icon="mdi:clock" width="24" height="24" />
						</div>
						<div class="info-text">
							<h3>Availability</h3>
							<p>Mon - Sat: 9:00 AM - 7:00 PM</p>
						</div>
					</div>

					<div class="info-card">
						<div class="icon-wrapper">
							<Icon icon="mdi:whatsapp" width="24" height="24" />
						</div>
						<div class="info-text">
							<h3>WhatsApp</h3>
							<a href="https://wa.me/6512345678">Chat with me</a>
						</div>
					</div>
				</div>

				<div class="social-connect">
					<h3>Connect on Social Media</h3>
					<div class="social-links">
						<a href="#" aria-label="Facebook">
							<Icon icon="mdi:facebook" width="20" height="20" />
						</a>
						<a href="#" aria-label="LinkedIn">
							<Icon icon="mdi:linkedin" width="20" height="20" />
						</a>
						<a href="#" aria-label="Instagram">
							<Icon icon="mdi:instagram" width="20" height="20" />
						</a>
					</div>
				</div>
			</div>

			<!-- Contact Form -->
			<div class="contact-form-wrapper">
				<form method="post" action="" class="contact-form" onsubmit={handleSubmit}>
					<div class="form-group">
						<label for="name">Full Name *</label>
						<input
							type="text"
							name="name"
							id="name"
							bind:value={formData.name}
							required
							placeholder="John Doe"
						/>
					</div>

					<div class="form-group">
						<label for="email">Email Address *</label>
						<input
							type="email"
							name="email"
							id="email"
							bind:value={formData.email}
							required
							placeholder="john@example.com"
						/>
					</div>

					<div class="form-group">
						<label for="phone">Phone Number *</label>
						<input
							type="tel"
							name="phone"
							id="phone"
							bind:value={formData.phone}
							required
							placeholder="+65 1234 5678"
							oninput={(e) => (e.target.value = e.target.value.replace(/[^0-9+\s-]/g, ''))}
							onkeypress={(e) => {
								const char = String.fromCharCode(e.which || e.keyCode);
								if (!/[0-9+\s-]/.test(char)) {
									e.preventDefault();
								}
							}}
						/>
					</div>

					<div class="form-group">
						<label for="subject">Subject *</label>
						<select name="subject" id="subject" bind:value={formData.subject} required>
							<option value="">Select a topic</option>
							<option value="portfolio-upgrading">Portfolio Upgrading</option>
							<option value="general-consultation">General Consultation</option>
							<option value="property-valuation">Property Valuation</option>
							<option value="investment-advice">Investment Advice</option>
							<option value="other">Other</option>
						</select>
					</div>

					<div class="form-group">
						<label for="referral">How did you hear about us? *</label>
						<select name="referral" id="referral" bind:value={formData.referral} required>
							<option value="">Select an option</option>
							<option value="google_search">Google Search</option>
							<option value="social_media">Social Media</option>
							<option value="referral">Referral from Friend/Family</option>
							<option value="previous_client">Previous Client</option>
							<option value="advertisement">Advertisement</option>
							<option value="other">Other</option>
						</select>

						{#if formData.referral === 'other'}
							<input
								type="text"
								name="referralOther"
								id="referralOther"
								bind:value={formData.referralOther}
								required
								placeholder="Please specify"
							/>
						{/if}
					</div>

					<div class="form-group">
						<label for="message">Message *</label>
						<textarea
							name="message"
							id="message"
							bind:value={formData.message}
							required
							rows="5"
							placeholder="Tell me about your real estate needs..."
						></textarea>
					</div>

					<div class="form-group checkbox-group">
						<label class="checkbox-label">
							<input
								name="consent"
								id="consent"
								type="checkbox"
								bind:checked={formData.consent}
								required
							/>
							<span>
								I agree to the <a href="/privacy-policy">Privacy Policy</a> and consent to the collection
								and use of my personal data for the purpose of responding to my inquiry.
							</span>
						</label>
					</div>

					{#if formStatus === 'success'}
						<div class="success-message">
							<Icon icon="mdi:check-circle" width="20" height="20" />
							Thank you! Your message has been sent successfully.
						</div>
					{:else if formStatus === 'error'}
						<div class="error-message">
							<Icon icon="mdi:alert-circle" width="20" height="20" />
							Oops! Something went wrong. Please try again.
						</div>
					{/if}

					<button
						type="submit"
						value="Submit"
						id="submit"
						class="submit-btn"
						disabled={formStatus === 'loading'}
					>
						{#if formStatus === 'loading'}
							<Icon icon="mdi:loading" class="spinner" width="20" height="20" />
							<span>Sending...</span>
						{:else}
							<span>Send Message</span>
							<Icon icon="mingcute:send-line" width="20" height="20" />
						{/if}
					</button>
				</form>
			</div>
		</div>
	</div>
</section>

<style lang="scss">
	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 20px;
	}

	.contact-hero {
		background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
		color: #000;
		padding: 80px 0 60px;
		text-align: center;

		.hero-title {
			font-size: 2.5rem;
			font-weight: 700;
			margin: 0 0 16px 0;
			line-height: 1.2;

			@media (max-width: 768px) {
				font-size: 1.75rem;
			}
		}

		.hero-subtitle {
			font-size: 20px;
			color: #666;
			max-width: 600px;
			margin: 0 auto;
			opacity: 0.9;

			@media (max-width: 768px) {
				font-size: 0.95rem;
				max-width: 400px;
			}
		}
	}

	.contact-section {
		padding: 80px 0;
		background: #f8f8f8;

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	:global(html[data-theme='dark']) .contact-section {
		background: #1a1a1a;
	}

	.contact-grid {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 80px;
		align-items: start;

		@media (max-width: 968px) {
			grid-template-columns: 1fr;
			gap: 60px;

			.contact-form-wrapper {
				order: -1;
			}
		}
	}

	.contact-info {
		h2 {
			font-size: 2rem;
			font-weight: 700;
			margin: 0 0 16px 0;

			@media (max-width: 768px) {
				font-size: 1.5rem;
			}
		}

		.intro-text {
			font-size: 1rem;
			line-height: 1.7;
			color: #666;
			margin: 0 0 40px 0;
		}
	}

	:global(html[data-theme='dark']) .contact-info {
		h2 {
			color: #d0d0d0;
		}

		.intro-text {
			color: #b0b0c0;
		}
	}

	.info-cards {
		display: flex;
		flex-direction: column;
		gap: 20px;
		margin-bottom: 40px;
	}

	.info-card {
		display: flex;
		align-items: flex-start;
		gap: 16px;
		padding: 20px;
		border-radius: 1rem;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);

		&:hover {
			background: #fafafa;
			transform: translateY(-4px);
			box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
		}

		.icon-wrapper {
			width: 48px;
			height: 48px;
			background: rgba(26, 26, 46, 0.08);
			border-radius: 50%;
			display: flex;
			align-items: center;
			justify-content: center;
			flex-shrink: 0;
			box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
			color: #1a1a1a;
		}

		.info-text {
			flex: 1;

			h3 {
				font-size: 1rem;
				font-weight: 600;
				margin: 0 0 4px 0;
				color: #1a1a1a;
			}

			p,
			a {
				font-size: 15px;
				color: #666;
				margin: 0;
				text-decoration: none;
				transition: color 0.3s ease;
			}

			a:hover {
				color: #1a1a1a;
			}
		}
	}

	:global(html[data-theme='dark']) .info-card {
		&:hover {
			background: #2a2a2a;
			box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
		}

		.icon-wrapper {
			background: rgba(200, 200, 220, 0.15);
			box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
			color: #d0d0d0;
		}

		.info-text {
			h3 {
				color: #e8e8f0;
			}

			p,
			a {
				color: #b0b0c0;
			}

			a:hover {
				color: #e8e8f0;
			}
		}
	}

	.social-connect {
		h3 {
			font-size: 18px;
			font-weight: 600;
			margin: 0 0 16px 0;
			color: #333;
		}

		.social-links {
			display: flex;
			gap: 12px;

			a {
				display: flex;
				align-items: center;
				justify-content: center;
				width: 40px;
				height: 40px;
				background: #fff;
				border: 1px solid #e0e0e0;
				border-radius: 50%;
				color: #1a1a1a;
				transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
				box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);

				&:hover {
					transform: translateY(-4px);
					background: #fafafa;
					box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
				}
			}

			@media (max-width: 768px) {
				gap: 8px;
			}
		}
	}

	:global(html[data-theme='dark']) .social-connect {
		h3 {
			color: #e8e8f0;
		}

		.social-links a {
			background: #2a2a2a;
			border: 1px solid #3a3a3a;
			color: #fff;
			box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);

			&:hover {
				background: #3a3a3a;
				border-color: #4a4a4a;
				box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
			}
		}
	}

	.contact-form-wrapper {
		background: #fff;
		padding: 40px;
		border-radius: 1.5rem;
		border: 1px solid #e0e0e0;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
	}

	:global(html[data-theme='dark']) .contact-form-wrapper {
		background: #1a1a1a;
		border: 1px solid rgba(255, 255, 255, 0.12);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
	}

	.contact-form {
		display: flex;
		flex-direction: column;
		gap: 24px;
	}

	.form-group {
		display: flex;
		flex-direction: column;
		gap: 8px;

		label {
			font-size: 14px;
			font-weight: 600;
			color: #333;
		}

		input,
		select,
		textarea {
			padding: 12px 16px;
			background: #fff;
			border: 1px solid #d0d0d0;
			border-radius: 0.8rem;
			font-size: 15px;
			font-family: 'Poppins', sans-serif;
			transition: all 0.3s ease;
			color: #333;

			&:focus {
				outline: none;
				background: #fff;
				border-color: #1a1a1a;
				box-shadow: 0 0 0 3px rgba(26, 26, 46, 0.1);
			}

			&::placeholder {
				color: rgba(0, 0, 0, 0.4);
			}
		}

		textarea {
			resize: vertical;
			min-height: 120px;
		}
	}

	:global(html[data-theme='dark']) .form-group {
		label {
			color: #d0d0d0;
		}

		input,
		select,
		textarea {
			background: #2a2a2a;
			border-color: #3a3a3a;
			color: #fff;

			&:focus {
				background: #4a4a4a;
				border-color: #6a6a6a;
			}

			&::placeholder {
				color: #888;
			}
		}
	}

	/* CHECKBOX GROUP */
	.checkbox-group {
		.checkbox-label {
			display: flex;
			align-items: flex-start;
			gap: 10px;
			font-size: 14px;
			font-weight: 400;
			cursor: pointer;

			input[type='checkbox'] {
				width: 18px;
				height: 18px;
				margin-top: 2px;
				cursor: pointer;
				accent-color: #1a1a1a;

				@media (max-width: 768px) {
					width: 16px;
					height: 16px;
				}
			}

			span {
				color: #666;
				line-height: 1.5;

				a {
					color: #1a1a1a;
					text-decoration: none;
					font-weight: 600;

					&:hover {
						text-decoration: underline;
					}
				}
			}
		}
	}

	:global(html[data-theme='dark']) .checkbox-group {
		.checkbox-label {
			input[type='checkbox'] {
				accent-color: #e8e8f0;
			}

			span {
				color: #b0b0c0;

				a {
					color: #e8e8f0;
				}
			}
		}
	}

	.success-message {
		display: flex;
		align-items: center;
		gap: 8px;
		padding: 12px 16px;
		background: rgba(43, 167, 108, 0.1);
		border: 1px solid rgba(43, 167, 108, 0.3);
		border-radius: 0.75rem;
		color: #2ba76c;
		font-size: 15px;
		box-shadow: none;
	}

	.error-message {
		display: flex;
		align-items: center;
		gap: 8px;
		padding: 12px 16px;
		background: rgba(211, 47, 47, 0.1);
		border: 1px solid rgba(211, 47, 47, 0.3);
		border-radius: 0.75rem;
		color: #d32f2f;
		font-size: 15px;
		box-shadow: none;
	}

	:global(html[data-theme='dark']) .success-message {
		background: rgba(76, 175, 80, 0.15);
		border-color: rgba(76, 175, 80, 0.3);
		color: #81c784;
		box-shadow: none;
	}

	:global(html[data-theme='dark']) .error-message {
		background: rgba(239, 83, 80, 0.15);
		border-color: rgba(239, 83, 80, 0.3);
		color: #ef5350;
		box-shadow: none;
	}

	.loading-message {
		padding: 12px 16px;
		background: #cfe2ff;
		color: #084298;
		border-radius: 0.25rem;
		font-size: 15px;
	}

	.submit-btn {
		display: flex;
		align-items: center;
		justify-content: center;
		gap: 8px;
		padding: 14px 32px;
		background: transparent;
		color: #1a1a1a;
		border: 2px solid #1a1a1a;
		border-radius: 0.75rem;
		font-size: 1rem;
		font-weight: 600;
		cursor: pointer;
		transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);

		&:hover:not(:disabled) {
			transform: translateY(-2px);
			box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
			border-color: #444;
		}

		&:disabled {
			opacity: 0.6;
			cursor: not-allowed;
			transform: none;
		}

		:global(.spinner) {
			animation: spin 1s linear infinite;
		}

		span {
			font-family: 'Poppins', sans-serif;
		}
	}

	:global(html[data-theme='dark']) .submit-btn {
		background: transparent;
		color: #e8e8f0;
		border-color: #e8e8f0;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.4);

		&:hover:not(:disabled) {
			background: rgba(220, 220, 240, 0.2);
			border-color: rgba(255, 255, 255, 0.25);
			box-shadow: 0 4px 8px rgba(0, 0, 0, 0.5);
		}
	}

	@keyframes spin {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}

	@media (max-width: 768px) {
		.contact-hero {
			padding: 120px 0 40px;

			h1 {
				font-size: 36px;
			}

			p {
				font-size: 16px;
			}
		}

		.contact-form-wrapper {
			padding: 24px;
		}
	}
</style>
