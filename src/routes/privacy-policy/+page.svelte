<script>
	import { onMount } from 'svelte';

	let containerVisible = $state(false);

	onMount(() => {
		setTimeout(() => {
			containerVisible = true;
		}, 100);
	});
</script>

<section class="privacy-policy">
	<div class="container" class:visible={containerVisible}>
		<h1>Privacy Policy</h1>

		<p>
			We are committed to safeguarding your privacy. We treat all personal data provided by you in
			strict confidence, and will only use your personal data in the manner set out in this privacy
			policy. This privacy policy applies to all personal data that you provide to us and the
			personal data we hold about you. This policy describes how we may collect, use, disclose,
			process and manage your personal data. Please DO NOT provide any personal data to us if you do
			not accept this policy.
		</p>

		<h2>How is the Collected Personal Data Used</h2>
		<p>Our primary goal in collecting your personal data is to serve you better. This includes:</p>
		<ul>
			<li>Providing you with the services that you have requested</li>
			<li>Contacting you for feedback after the provision of our services</li>
		</ul>

		<p>We may also use your personal data for purposes connected or relevant to our business.</p>
		<p>
			If you have consented, we may use your personal data for the purposes of marketing our
			products and services e.g. informing you of our latest activities, special offers and
			promotions. In order for us to market products and services which are of special interest and
			relevance to you, we may analyse and rely on your overall interaction with us (such as but not
			limited to your participation in promotions or events and your interactions with us).
		</p>
		<p>
			If you have contacted us with any complaints, feedback, comments, or suggestions, we may use
			and disclose your personal data (including your contact history) to respond to you.
		</p>
		<p>
			When using your personal data to contact you for the above purposes, we may contact you via
			regular mail, fax, e-mail, SMS, telephone, or any other means.
		</p>

		<h2>Disclosure of Information</h2>
		<p>We will not sell your data to third parties.</p>

		<h2>Security</h2>
		<p>
			All information gathered is stored in our secure servers and all precautions will be taken to
			ensure that the information you provide is protected against unauthorised or unintended
			access. However, we cannot be held responsible for unauthorised or unintended access that is
			beyond our control.
		</p>

		<h2>Amendment of Privacy Policy</h2>
		<p>
			We may amend this privacy policy from time to time. The updated privacy policy will be made
			available here.
		</p>

		<h2>Your Rights</h2>
		<p>
			If you do not accept the amended privacy policy or if you wish to withdraw any consent you
			have given us at any time, or if you wish to update or have access to your personal data, you
			may contact us at:
		</p>

		<div class="contact">
			<p><strong>Attention to:</strong> Derrick Teo</p>
			<p>
				<strong>Email:</strong> <a href="mailto:derrickteobiz@gmail.com">derrickteobiz@gmail.com</a>
			</p>
			<p><strong>Phone:</strong> <a href="tel:+6581217754">+65 8121 7754</a></p>
		</div>

		<p>
			All requests for correction or for access to your personal data must be in writing to
			<a href="mailto:derrickteobiz@gmail.com">derrickteobiz@gmail.com</a>. We will endeavor to
			respond to your request within 30 days, and if that is not possible, we will inform you of the
			time by which we will respond to you.
		</p>
		<p>
			We may be prevented by law from complying with any request that you may make. We may also
			decline any request that you may make if the law permits us to do so.
		</p>
		<p>
			In many circumstances, we need to use your personal data in order for us to provide you with
			products or services which you require. If you do not provide us with the required personal
			data, or if you withdraw your consent to our use and/or disclosure of your personal data for
			these purposes, it may not be possible for us to continue to serve you or provide you with the
			products and services that you require.
		</p>

		<h2>Governing Law</h2>
		<p>
			This privacy policy is governed by the laws of Singapore. You consent to submit to the
			exclusive jurisdiction of the Courts of Singapore in any dispute relating to this privacy
			policy.
		</p>
	</div>
</section>

<style lang="scss">
	.privacy-policy {
		background-color: #f8f8f8;
		color: #222;
		padding: 4rem 1rem;

		.container {
			max-width: 800px;
			margin: 0 auto;
			background: #fff;
			padding: 3rem 2rem;
			border-radius: 1rem;
			border: 1px solid #e0e0e0;
			box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
			opacity: 0;
			transform: translateY(30px);
			transition: all 0.6s ease;

			&.visible {
				opacity: 1;
				transform: translateY(0);
			}

			@media (max-width: 768px) {
				padding: 2rem 1.5rem;
			}
		}

		h1 {
			font-size: 2rem;
			font-weight: 700;
			margin-bottom: 1.5rem;
			text-align: center;
			color: #111;
		}

		h2 {
			font-size: 1.4rem;
			margin-top: 2.5rem;
			margin-bottom: 1rem;
			color: #333;
		}

		p {
			font-size: 1rem;
			line-height: 1.7;
			margin-bottom: 1rem;
		}

		ul {
			list-style: disc;
			padding-left: 2rem;
			margin-bottom: 1rem;

			li {
				margin-bottom: 0.5rem;
			}
		}

		.contact {
			background: #f9f9f9;
			padding: 1rem 1.5rem;
			border-left: 4px solid #000;
			border-radius: 0.5rem;
			margin: 1rem 0;

			a {
				color: #0077ff;
				text-decoration: none;

				&:hover {
					text-decoration: underline;
				}
			}

			@media (max-width: 768px) {
				padding: 1rem;
			}
		}
	}

	:global(html[data-theme='dark']) .privacy-policy {
		background-color: #1a1a1a;
		color: #d0d0d0;
	}

	:global(html[data-theme='dark']) .privacy-policy .container {
		background: #1a1a1a;
		border: 1px solid rgba(255, 255, 255, 0.12);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
	}

	/* HEADINGS */
	.privacy-policy h1 {
		font-size: 2rem;
		font-weight: 700;
		margin-bottom: 1.5rem;
		text-align: center;
		color: #111;

		@media (max-width: 768px) {
			font-size: 1.5rem;
		}
	}

	:global(html[data-theme='dark']) .privacy-policy h1 {
		color: #e8e8f0;
	}

	.privacy-policy h2 {
		font-size: 1.4rem;
		margin-top: 2.5rem;
		margin-bottom: 1rem;
		color: #333;

		@media (max-width: 768px) {
			font-size: 1.1rem;
			margin-top: 2rem;
		}
	}

	:global(html[data-theme='dark']) .privacy-policy h2 {
		color: #d0d0d0;
	}

	/* PARAGRAPHS */
	.privacy-policy p {
		line-height: 1.7;
		margin-bottom: 1rem;
		color: #666;
	}

	:global(html[data-theme='dark']) .privacy-policy p {
		color: #a0a0b0;
	}

	/* LIST ITEMS */
	.privacy-policy ul {
		list-style: disc;
		padding-left: 2rem;
		margin-bottom: 1rem;

		li {
			margin-bottom: 0.5rem;
			color: #666;
		}
	}

	:global(html[data-theme='dark']) .privacy-policy ul li {
		color: #a0a0b0;
	}

	/* CONTACT CARD */
	.privacy-policy .contact {
		background: #f9f9f9;
		padding: 1.5rem;
		border-left: 4px solid #1a1a1a;
		border-radius: 0.5rem;
		margin: 1.5rem 0;
		box-shadow: none;

		p {
			margin-bottom: 0.75rem;
			color: #333;
		}

		a {
			color: #0077ff;
			text-decoration: none;
			font-weight: 600;
			transition: all 0.3s ease;

			&:hover {
				color: #0059cc;
				text-decoration: underline;
			}
		}

		@media (max-width: 768px) {
			padding: 1rem;
		}
	}

	:global(html[data-theme='dark']) .privacy-policy .contact {
		background: #2a2a2a;
		border-left: 4px solid #b0b0d0;
		box-shadow: none;

		p {
			color: #d0d0d0;
		}

		a {
			color: #6ba3ff;

			&:hover {
				color: #91bfff;
			}
		}
	}
</style>
