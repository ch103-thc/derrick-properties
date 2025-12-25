<script>
	import { onMount } from 'svelte';
	import Icon from '@iconify/svelte';

	let isVisible = $state(false);
	let journeyVisible = $state(false);
	let landlordVisible = $state(false);
	let tenantVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						if (entry.target.classList.contains('hero-section')) {
							isVisible = true;
						}
						if (entry.target.classList.contains('journey-section')) {
							journeyVisible = true;
						}
						if (entry.target.classList.contains('landlord-section')) {
							landlordVisible = true;
						}
						if (entry.target.classList.contains('tenant-section')) {
							tenantVisible = true;
						}
					}
				});
			},
			{ threshold: 0.1 }
		);

		const heroSection = document.querySelector('.hero-section');
		const journeySection = document.querySelector('.journey-section');
		const landlordSection = document.querySelector('.landlord-section');
		const tenantSection = document.querySelector('.tenant-section');

		if (heroSection) observer.observe(heroSection);
		if (journeySection) observer.observe(journeySection);
		if (landlordSection) observer.observe(landlordSection);
		if (tenantSection) observer.observe(tenantSection);

		return () => observer.disconnect();
	});

	const landlordServices = [
		{
			icon: 'mdi:account-search',
			title: 'Tenant Profiling',
			description:
				'We carefully screen tenants through income verification, background checks, and intent-to-stay — so you get the right fit for your property.'
		},
		{
			icon: 'mdi:currency-usd',
			title: 'Strategic Rental Pricing',
			description:
				'Our market analysis ensures your unit is competitively priced, attracting quality tenants without undervaluing your space.'
		},
		{
			icon: 'mdi:camera-image',
			title: 'High-Impact Listing & Marketing',
			description:
				'From quality photos to targeted rental platform listings, we showcase your property to the right audience — fast.'
		},
		{
			icon: 'mdi:file-document-edit',
			title: 'Negotiation & Documentation',
			description:
				'We handle negotiations professionally and ensure all terms are documented clearly in the tenancy agreement — including clauses that protect your rights.'
		},
		{
			icon: 'mdi:account-heart',
			title: 'Full-Tenancy Support',
			description:
				"We don't stop at signing. We remain available throughout the lease to help mediate disputes, coordinate handovers, and ensure smooth renewals or exits."
		}
	];

	const tenantServices = [
		{
			icon: 'mdi:map-marker-radius',
			title: 'Location & Budget Matching',
			description:
				"Tell us your priorities — proximity to MRT, schools, CBD, etc. — and we'll match you to the right home, within your rental budget."
		},
		{
			icon: 'mdi:calendar-check',
			title: 'Viewing Scheduling & Advice',
			description:
				"We line up viewings efficiently and provide expert insights on the pros and cons of each unit, not just what's visible."
		},
		{
			icon: 'mdi:file-check',
			title: 'Lease Term Clarity',
			description:
				'We help you understand every clause — from deposit terms to utility payments — so there are no hidden surprises.'
		},
		{
			icon: 'mdi:home-heart',
			title: 'Smooth Move-In & Ongoing Support',
			description:
				"Need help with handover documentation? Key collection? Minor issues post-move? We're just a message away — even after the lease is signed."
		}
	];
</script>

<svelte:head>
	<title>Renting a Property - For Landlords & Tenants | D'Home Series</title>
	<meta
		name="description"
		content="Renting made simple, safe, and strategic. Comprehensive rental assistance for both landlords and tenants with full-tenancy support."
	/>
</svelte:head>

<!-- Hero Section -->
<section class="hero-section" class:visible={isVisible}>
	<div class="container">
		<div class="hero-content">
			<h1>Renting a Property</h1>
			<p class="hero-subtitle">Renting Made Simple, Safe & Strategic</p>
			<p class="hero-tagline">For Landlords & Tenants Who Want More Than Just a Lease</p>
			<p class="hero-description">
				Whether you're a landlord looking to protect your asset or a tenant searching for the
				perfect home, renting should be simple, secure, and stress-free.
			</p>
			<p class="hero-description">
				At D'Home Series, we go beyond just matching people with places. We provide a comprehensive
				rental experience — guiding you through the entire tenancy journey, from start to finish.
			</p>
		</div>
	</div>
</section>

<!-- Journey Section -->
<section class="journey-section">
	<div class="container">
		<div class="journey-content">
			<h2>We're With You for the Whole Journey</h2>
			<p class="journey-intro">Most agents disappear after the contract is signed. We don't.</p>
			<p>
				Whether you're a landlord or tenant, our goal is to build long-term trust — and that means
				being there for you throughout the tenancy.
			</p>
			<p class="journey-commitment">
				From pre-tenancy advisory, mid-term check-ins, to exit planning and renewal decisions —
				we're here to support you at every milestone.
			</p>
		</div>
	</div>
</section>

<!-- Testimonials Section -->
<section class="testimonials-section">
	<div class="container">
		<div class="testimonials-grid">
			<div class="testimonial-card" class:visible={journeyVisible}>
				<div class="testimonial-header">
					<Icon icon="mdi:format-quote-open" width="32" height="32" />
				</div>
				<p class="testimonial-text">
					David & Audrie helped us rent out our unit within a week — and even assisted with tenant
					issues months into the lease. They're professional, patient, and proactive.
				</p>
				<p class="testimonial-author">
					<strong>Jonathan</strong><br />
					Landlord (D15 2BR Condo)
				</p>
			</div>

			<div class="testimonial-card" class:visible={journeyVisible} style="--delay: 1">
				<div class="testimonial-header">
					<Icon icon="mdi:format-quote-open" width="32" height="32" />
				</div>
				<p class="testimonial-text">
					They made the whole renting process so smooth. We were new expats in Singapore and had no
					clue about tenancy agreements — David & Audrie explained everything clearly and even
					helped us settle in.
				</p>
				<p class="testimonial-author">
					<strong>Ana & Marcos</strong><br />
					Tenants (Tiong Bahru)
				</p>
			</div>
		</div>
	</div>
</section>

<!-- Landlord Section -->
<section class="landlord-section">
	<div class="container">
		<div class="section-header">
			<Icon icon="mdi:home-account" width="48" height="48" />
			<h2>For Landlords: Your Property, Our Priority</h2>
			<p>
				We help landlords not only secure tenants quickly, but also protect your rental income,
				asset condition, and peace of mind.
			</p>
		</div>

		<div class="services-grid">
			{#each landlordServices as service, i}
				<div class="service-card" class:visible={landlordVisible} style="--delay: {i}">
					<div class="service-icon">
						<Icon icon={service.icon} width="32" height="32" />
					</div>
					<h3>{service.title}</h3>
					<p>{service.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Tenant Section -->
<section class="tenant-section">
	<div class="container">
		<div class="section-header">
			<Icon icon="mdi:account-key" width="48" height="48" />
			<h2>For Tenants: Rent With Confidence, Not Confusion</h2>
			<p>
				We guide tenants through every step so you can rent with clarity and confidence — whether
				you're a local, PR, or expat.
			</p>
		</div>

		<div class="services-grid">
			{#each tenantServices as service, i}
				<div class="service-card" class:visible={tenantVisible} style="--delay: {i}">
					<div class="service-icon">
						<Icon icon={service.icon} width="32" height="32" />
					</div>
					<h3>{service.title}</h3>
					<p>{service.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- CTA Section -->
<section class="cta-section">
	<div class="container">
		<div class="cta-content">
			<h2>Ready to Rent With Confidence?</h2>
			<p>
				Book a Rental Consultation with David & Audrie today. Let's make your rental journey simple,
				clear, and stress-free — from keys to contracts and everything in between.
			</p>
			<a href="/contact" class="cta-button">Book My Consultation</a>
		</div>
	</div>
</section>

<style lang="scss">
	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 20px;
	}

	/* Hero Section */
	.hero-section {
		padding: 80px 0 60px;
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.8s ease;

		&.visible {
			opacity: 1;
			transform: translateY(0);
		}

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	.hero-content {
		text-align: center;
		max-width: 900px;
		margin: 0 auto;

		h1 {
			font-size: 48px;
			margin: 0 0 16px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 32px;
			}
		}

		.hero-subtitle {
			font-size: 28px;
			margin: 0 0 8px 0;
			color: #3a3546;
			font-weight: 600;

			@media (max-width: 768px) {
				font-size: 22px;
			}
		}

		.hero-tagline {
			font-size: 18px;
			margin: 0 0 24px 0;
			color: #666;
			font-style: italic;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.hero-description {
			font-size: 18px;
			line-height: 1.7;
			color: #666;
			margin: 0 0 20px 0;

			&:last-child {
				margin-bottom: 0;
			}

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}
	}

	:global(html[data-theme='dark']) .hero-content {
		h1 {
			color: #fff;
		}

		.hero-subtitle {
			color: #fff;
		}

		.hero-tagline,
		.hero-description {
			color: #aaa;
		}
	}

	/* Journey Section */
	.journey-section {
		padding: 80px 0;
		background: #f5f5f5;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.journey-content {
		max-width: 800px;
		margin: 0 auto;
		text-align: center;

		h2 {
			font-size: 32px;
			margin: 0 0 16px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 24px;
			}
		}

		.journey-intro {
			font-size: 20px;
			font-weight: 600;
			color: #3a3546;
			margin: 0 0 16px 0;

			@media (max-width: 768px) {
				font-size: 18px;
			}
		}

		p {
			font-size: 18px;
			line-height: 1.7;
			color: #666;
			margin: 0 0 16px 0;

			&:last-child {
				margin-bottom: 0;
			}

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.journey-commitment {
			font-size: 18px;
			color: #333;
			font-weight: 500;
			margin-top: 24px;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}
	}

	:global(html[data-theme='dark']) .journey-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .journey-content {
		h2 {
			color: #fff;
		}

		.journey-intro {
			color: #fff;
		}

		p {
			color: #aaa;
		}

		.journey-commitment {
			color: #fff;
		}
	}

	/* Testimonials Section */
	.testimonials-section {
		padding: 80px 0;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.testimonials-grid {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 32px;
		max-width: 1100px;
		margin: 0 auto;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
			gap: 24px;
		}
	}

	.testimonial-card {
		background: #f5f5f5;
		border-radius: 12px;
		padding: 32px;
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.6s ease;

		&.visible {
			opacity: 1;
			transform: translateY(0);
			transition-delay: calc(var(--delay, 0) * 0.2s);
		}

		@media (max-width: 768px) {
			padding: 24px;
		}
	}

	.testimonial-header {
		color: #3a3546;
		margin-bottom: 16px;
	}

	.testimonial-text {
		font-size: 16px;
		line-height: 1.7;
		color: #333;
		margin: 0 0 20px 0;
		font-style: italic;

		@media (max-width: 768px) {
			font-size: 15px;
		}
	}

	.testimonial-author {
		font-size: 15px;
		color: #666;
		margin: 0;

		@media (max-width: 768px) {
			font-size: 14px;
		}

		strong {
			color: #3a3546;
		}
	}

	:global(html[data-theme='dark']) .testimonial-card {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .testimonial-header {
		color: #fff;
	}

	:global(html[data-theme='dark']) .testimonial-text {
		color: #aaa;
	}

	:global(html[data-theme='dark']) .testimonial-author {
		color: #aaa;

		strong {
			color: #fff;
		}
	}

	/* Landlord & Tenant Sections */
	.landlord-section,
	.tenant-section {
		padding: 80px 0;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.landlord-section {
		background: #f5f5f5;
	}

	:global(html[data-theme='dark']) .landlord-section {
		background: #27272a;
	}

	.section-header {
		text-align: center;
		max-width: 800px;
		margin: 0 auto 48px;

		:global(svg) {
			color: #3a3546;
			margin-bottom: 16px;
		}

		h2 {
			font-size: 32px;
			margin: 0 0 16px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 24px;
			}
		}

		p {
			font-size: 18px;
			line-height: 1.7;
			color: #666;
			margin: 0;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}
	}

	:global(html[data-theme='dark']) .section-header {
		:global(svg) {
			color: #fff;
		}

		h2 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	.services-grid {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 24px;
		max-width: 1100px;
		margin: 0 auto;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
		}
	}

	.service-card {
		background: #fff;
		border-radius: 12px;
		padding: 32px;
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.6s ease;

		&.visible {
			opacity: 1;
			transform: translateY(0);
			transition-delay: calc(var(--delay) * 0.1s);
		}

		@media (max-width: 768px) {
			padding: 24px;
		}

		h3 {
			font-size: 20px;
			margin: 0 0 12px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 18px;
			}
		}

		p {
			font-size: 16px;
			line-height: 1.7;
			color: #666;
			margin: 0;

			@media (max-width: 768px) {
				font-size: 15px;
			}
		}
	}

	.service-icon {
		width: 56px;
		height: 56px;
		background: #3a3546;
		color: #fff;
		border-radius: 12px;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 16px;
	}

	:global(html[data-theme='dark']) .service-card {
		background: #1a1a1a;

		h3 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .service-icon {
		background: #fff;
		color: #1a1a1a;
	}

	/* CTA Section */
	.cta-section {
		padding: 80px 0;
		background: #f5f5f5;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.cta-content {
		max-width: 800px;
		margin: 0 auto;
		text-align: center;

		h2 {
			font-size: 32px;
			margin: 0 0 24px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 24px;
			}
		}

		p {
			font-size: 18px;
			line-height: 1.7;
			color: #666;
			margin: 0 0 32px 0;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.cta-button {
			display: inline-block;
			padding: 16px 32px;
			background: #3a3546;
			color: #fff;
			border-radius: 12px;
			font-weight: 600;
			font-size: 18px;
			text-decoration: none;
			cursor: pointer;
			transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
			box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);

			@media (hover: hover) and (pointer: fine) {
				&:hover {
					box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
					background: #333;
					transform: translateY(-2px);
				}
			}

			@media (max-width: 768px) {
				font-size: 16px;
				padding: 14px 28px;
			}
		}
	}

	:global(html[data-theme='dark']) .cta-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .cta-content {
		h2 {
			color: #fff;
		}

		p {
			color: #aaa;
		}

		.cta-button {
			background: #fff;
			color: #1a1a1a;
			box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);

			@media (hover: hover) and (pointer: fine) {
				&:hover {
					box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
					background: #e0e0e0;
				}
			}
		}
	}
</style>
