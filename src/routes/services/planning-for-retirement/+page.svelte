<script>
	import { onMount } from 'svelte';
	import Icon from '@iconify/svelte';

	let isVisible = $state(false);
	let processVisible = $state(false);
	let benefitsVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						if (entry.target.classList.contains('hero-section')) {
							isVisible = true;
						}
						if (entry.target.classList.contains('process-section')) {
							processVisible = true;
						}
						if (entry.target.classList.contains('benefits-section')) {
							benefitsVisible = true;
						}
					}
				});
			},
			{ threshold: 0.1 }
		);

		const heroSection = document.querySelector('.hero-section');
		const processSection = document.querySelector('.process-section');
		const benefitsSection = document.querySelector('.benefits-section');

		if (heroSection) observer.observe(heroSection);
		if (processSection) observer.observe(processSection);
		if (benefitsSection) observer.observe(benefitsSection);

		return () => observer.disconnect();
	});

	const processSteps = [
		{
			icon: 'mdi:chart-line',
			title: 'Assess Your Current Financial Position',
			description:
				'We look at your CPF balances, property equity, mortgage structure, and total debt servicing ratio (TDSR/MSR) to understand your real position — not just on paper, but in potential.'
		},
		{
			icon: 'mdi:calculator',
			title: 'Calculate Retirement Gaps',
			description:
				'We help you determine how much you need for the lifestyle you want, and identify any shortfall between your future needs and current trajectory.'
		},
		{
			icon: 'mdi:home-analytics',
			title: 'Model Property-Backed Solutions',
			description:
				"Whether it's right-sizing, asset progression, or restructuring your portfolio, we'll build a roadmap using property as your primary wealth vehicle — supported by actual case studies and numbers."
		},
		{
			icon: 'mdi:cash-multiple',
			title: 'Optimise for Cash Flow and Exit',
			description:
				"Retirement isn't just about getting there — it's about staying there. We'll show you how to generate sustainable cash flow through rental income, reduce liabilities, and plan exit strategies that support longevity and legacy."
		},
		{
			icon: 'mdi:timeline-clock',
			title: 'Timeline Your Early Retirement',
			description:
				"We'll map out the milestones needed for you to retire earlier than traditional norms — possibly as early as 45 or 55 — based on your profile."
		}
	];

	const benefits = [
		{
			title: 'Property as Wealth Asset',
			description:
				'We help you work towards retirement proactively through property as a wealth asset, not a liability.'
		},
		{
			title: 'Data-Driven Approach',
			description:
				'We combine hard data, holistic planning, and deep market knowledge with a simple, clear approach.'
		},
		{
			title: 'No Jargon, No Pressure',
			description:
				'Clear, straightforward guidance focused on your goals without overwhelming complexity.'
		}
	];
</script>

<svelte:head>
	<title>Planning for Retirement - W.A.T.E.R Concept | D'Home Series</title>
	<meta
		name="description"
		content="Retire earlier with our proven W.A.T.E.R Concept. Strategic property planning for long-term security and sustainable retirement income."
	/>
</svelte:head>

<!-- Hero Section -->
<section class="hero-section" class:visible={isVisible}>
	<div class="container">
		<div class="hero-content">
			<h1>Retirement Planning</h1>
			<p class="hero-subtitle">Live Free. Retire Early. Plan With W.A.T.E.R.</p>
			<p class="hero-description">
				Retirement isn't just a finish line — it's a lifestyle you deserve to enjoy on your own
				terms, earlier than you think.
			</p>
			<p class="hero-description">
				At D'Home Series, we specialise in helping homeowners and aspiring investors plan for
				retirement using our proven <strong>W.A.T.E.R Concept</strong> — a property-based strategy
				that turns your real estate assets into a retirement engine.
			</p>
		</div>
	</div>
</section>

<!-- W.A.T.E.R Concept Intro -->
<section class="water-intro-section">
	<div class="container">
		<div class="water-content">
			<div class="water-text">
				<h2>What is the W.A.T.E.R Concept?</h2>
				<p>
					<strong>W.A.T.E.R</strong> stands for <strong
						>Wealth Accumulation Towards Early Retirement</strong
					>. It's a structured property planning strategy we've developed to help individuals and
					families build up sustainable wealth and passive income — not by working harder, but by
					planning smarter.
				</p>
				<p>
					We've applied the W.A.T.E.R Concept to help over 50 couples and individuals move
					significantly closer to their retirement goals, by optimising the way they use, hold, and
					grow their property assets.
				</p>
				<a href="/water-concept" class="water-link">
					Read more about the W.A.T.E.R Concept
					<Icon icon="mdi:arrow-right" width="20" height="20" />
				</a>
			</div>
			<!-- Image placeholder - add your image here -->
			<div class="water-image">
				<img src="/img/water-process.jpg" alt="W.A.T.E.R Concept Process" loading="lazy" />
			</div>
		</div>
	</div>
</section>

<!-- Process Section -->
<section class="process-section">
	<div class="container">
		<h2 class="section-title">What Happens in Retirement Planning?</h2>
		<p class="section-description">
			Your Retirement Planning Session is a focused consultation where we:
		</p>

		<div class="process-grid">
			{#each processSteps as step, i}
				<div class="process-card" class:visible={processVisible} style="--delay: {i}">
					<div class="process-icon">
						<Icon icon={step.icon} width="32" height="32" />
					</div>
					<h3>{step.title}</h3>
					<p>{step.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Testimonial Section -->
<section class="testimonial-section">
	<div class="container">
		<div class="testimonial-card">
			<div class="testimonial-header">
				<Icon icon="mdi:format-quote-open" width="40" height="40" />
			</div>
			<p class="testimonial-text">
				David & Audrie helped us understand how our property could actually work for us. We always
				assumed retirement was decades away — but after following their W.A.T.E.R roadmap, we're
				now planning to retire 10 years earlier than we thought.
			</p>
			<p class="testimonial-author">
				<strong>Sharon & Andy</strong><br />
				Age 44 & 47, Executive Professionals
			</p>
		</div>
	</div>
</section>

<!-- Benefits Section -->
<section class="benefits-section">
	<div class="container">
		<h2 class="section-title">Why Retirement Planning is Different With Us</h2>
		<p class="section-description">
			While others talk about waiting for retirement, we help you work towards it proactively
			through property as a wealth asset, not a liability.
		</p>

		<div class="benefits-grid">
			{#each benefits as benefit, i}
				<div class="benefit-card" class:visible={benefitsVisible} style="--delay: {i}">
					<h3>{benefit.title}</h3>
					<p>{benefit.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- CTA Section -->
<section class="cta-section">
	<div class="container">
		<div class="cta-content">
			<h2>Ready to Retire Earlier — and Better?</h2>
			<p>
				Schedule your 1-to-1 Retirement Planning Session with us today. Let us help you map out
				your retirement journey using the W.A.T.E.R Concept — the earlier you start, the stronger
				your flow.
			</p>
			<a href="/contact" class="cta-button">Schedule My Appointment Now</a>
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
			font-size: 24px;
			margin: 0 0 24px 0;
			color: #3a3546;
			font-weight: 600;

			@media (max-width: 768px) {
				font-size: 18px;
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

			strong {
				color: #3a3546;
				font-weight: 600;
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

		.hero-description {
			color: #aaa;

			strong {
				color: #fff;
			}
		}
	}

	/* W.A.T.E.R Intro Section */
	.water-intro-section {
		padding: 80px 0;
		background: #f5f5f5;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.water-content {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 60px;
		align-items: center;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
			gap: 40px;
		}
	}

	.water-text {
		h2 {
			font-size: 32px;
			margin: 0 0 24px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 24px;
			}
		}

		p {
			font-size: 16px;
			line-height: 1.7;
			color: #666;
			margin: 0 0 20px 0;

			&:last-of-type {
				margin-bottom: 24px;
			}

			@media (max-width: 768px) {
				font-size: 15px;
			}

			strong {
				color: #3a3546;
				font-weight: 600;
			}
		}

		.water-link {
			display: inline-flex;
			align-items: center;
			gap: 8px;
			color: #3a3546;
			font-weight: 600;
			text-decoration: none;
			transition: all 0.3s ease;

			@media (hover: hover) and (pointer: fine) {
				&:hover {
					gap: 12px;
				}
			}
		}
	}

	.water-image {
		width: 100%;
		height: 400px;
		border-radius: 12px;
		overflow: hidden;
		box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);

		@media (max-width: 768px) {
			height: 300px;
			order: -1;
		}

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
		}
	}

	:global(html[data-theme='dark']) .water-intro-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .water-text {
		h2 {
			color: #fff;
		}

		p {
			color: #aaa;

			strong {
				color: #fff;
			}
		}

		.water-link {
			color: #fff;
		}
	}

	/* Process Section */
	.process-section {
		padding: 80px 0;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.section-title {
		font-size: 32px;
		text-align: center;
		margin: 0 0 16px 0;
		color: #333;

		@media (max-width: 768px) {
			font-size: 24px;
		}
	}

	.section-description {
		font-size: 18px;
		text-align: center;
		color: #666;
		margin: 0 0 48px 0;
		max-width: 800px;
		margin-left: auto;
		margin-right: auto;

		@media (max-width: 768px) {
			font-size: 16px;
			margin-bottom: 32px;
		}
	}

	:global(html[data-theme='dark']) .section-title {
		color: #fff;
	}

	:global(html[data-theme='dark']) .section-description {
		color: #aaa;
	}

	.process-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 24px;
		max-width: 900px;
		margin: 0 auto;
	}

	.process-card {
		background: #f5f5f5;
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

	.process-icon {
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

	:global(html[data-theme='dark']) .process-card {
		background: #27272a;

		h3 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .process-icon {
		background: #fff;
		color: #1a1a1a;
	}

	/* Testimonial Section */
	.testimonial-section {
		padding: 80px 0;
		background: #f5f5f5;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.testimonial-card {
		max-width: 900px;
		margin: 0 auto;
		background: #fff;
		border-radius: 12px;
		padding: 48px;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);

		@media (max-width: 768px) {
			padding: 32px 24px;
		}
	}

	.testimonial-header {
		color: #3a3546;
		margin-bottom: 24px;
	}

	.testimonial-text {
		font-size: 18px;
		line-height: 1.8;
		color: #333;
		margin: 0 0 24px 0;
		font-style: italic;

		@media (max-width: 768px) {
			font-size: 16px;
		}
	}

	.testimonial-author {
		font-size: 16px;
		color: #666;
		margin: 0;

		@media (max-width: 768px) {
			font-size: 15px;
		}

		strong {
			color: #3a3546;
		}
	}

	:global(html[data-theme='dark']) .testimonial-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .testimonial-card {
		background: #1a1a1a;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
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

	/* Benefits Section */
	.benefits-section {
		padding: 80px 0;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.benefits-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 24px;
		max-width: 1000px;
		margin: 0 auto;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
			gap: 16px;
		}
	}

	.benefit-card {
		background: #f5f5f5;
		border-radius: 12px;
		padding: 32px;
		text-align: center;
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
			font-size: 18px;
			margin: 0 0 12px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		p {
			font-size: 15px;
			line-height: 1.6;
			color: #666;
			margin: 0;

			@media (max-width: 768px) {
				font-size: 14px;
			}
		}
	}

	:global(html[data-theme='dark']) .benefit-card {
		background: #27272a;

		h3 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
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