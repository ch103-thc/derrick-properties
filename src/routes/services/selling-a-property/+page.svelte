<script>
	import { onMount } from 'svelte';
	import Icon from '@iconify/svelte';

	let isVisible = $state(false);
	let calculationsVisible = $state(false);
	let strategyVisible = $state(false);
	let benefitsVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						if (entry.target.classList.contains('hero-section')) {
							isVisible = true;
						}
						if (entry.target.classList.contains('calculations-section')) {
							calculationsVisible = true;
						}
						if (entry.target.classList.contains('strategy-section')) {
							strategyVisible = true;
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
		const calculationsSection = document.querySelector('.calculations-section');
		const strategySection = document.querySelector('.strategy-section');
		const benefitsSection = document.querySelector('.benefits-section');

		if (heroSection) observer.observe(heroSection);
		if (calculationsSection) observer.observe(calculationsSection);
		if (strategySection) observer.observe(strategySection);
		if (benefitsSection) observer.observe(benefitsSection);

		return () => observer.disconnect();
	});

	const calculations = [
		{
			icon: 'mdi:calculator-variant',
			title: 'Net Sales Proceeds Calculation',
			description:
				"Know exactly how much you'll walk away with after CPF refunds, outstanding loans, and legal/agent fees."
		},
		{
			icon: 'mdi:cash-multiple',
			title: 'Cash Flow Projection for Next Home',
			description:
				"Whether you're upgrading or right-sizing, we project your cash-on-hand post-sale to help with your next move."
		},
		{
			icon: 'mdi:timeline-clock-outline',
			title: 'Timeline Mapping',
			description:
				'We sync your sale, purchase, and move-in plans — avoiding overlapping costs and unnecessary stress.'
		}
	];

	const strategies = [
		{
			icon: 'mdi:home-edit',
			title: 'Professional Home Staging',
			description: "We enhance your home's appeal to create emotional triggers for buyers."
		},
		{
			icon: 'mdi:camera',
			title: 'High-Impact Visual Marketing',
			description:
				'Sharp photography, lifestyle videos, and even drone visuals when needed — because first impressions drive viewings.'
		},
		{
			icon: 'mdi:bullhorn',
			title: 'Digital & Social Media Campaigns',
			description:
				'Your home is promoted on top property portals and social media platforms like Instagram, Facebook, and TikTok — reaching active and passive buyers.'
		},
		{
			icon: 'mdi:chart-line',
			title: 'Pricing Psychology & Demand Management',
			description:
				'We use market data and behavioural pricing techniques to spark urgency and manage offers.'
		},
		{
			icon: 'mdi:handshake',
			title: 'Negotiation That Protects Your Interests',
			description:
				'Our negotiation approach focuses not just on price, but also timeline and terms — giving you leverage and flexibility.'
		}
	];

	const benefits = [
		{
			icon: 'mdi:lightbulb-on',
			title: 'Strategists',
			description: 'To advise when and how to sell'
		},
		{
			icon: 'mdi:chart-box',
			title: 'Planners',
			description: 'Who help you avoid financial shocks'
		},
		{
			icon: 'mdi:account-heart',
			title: 'Partners',
			description: 'Who genuinely care about your next chapter'
		}
	];
</script>

<svelte:head>
	<title>Selling a Property - Strategic Guidance | D'Home Series</title>
	<meta
		name="description"
		content="Strategic guidance to position, market, and sell your property for the best price. Professional staging, pricing strategy, and timeline planning."
	/>
</svelte:head>

<!-- Hero Section -->
<section class="hero-section" class:visible={isVisible}>
	<div class="container">
		<div class="hero-content">
			<h1>Selling My Property</h1>
			<p class="hero-subtitle">
				More Than Selling Homes and Selling Property — We Deliver Results Beyond Expectations.
			</p>
			<p class="hero-description">
				Selling your property isn't just about putting it on the market — it's a delicate
				combination of strategy, timing, and execution that can impact your next purchase, your cash
				flow, and even your peace of mind.
			</p>
			<p class="hero-description">
				At D'Home Series, we don't just sell homes. We create results through a carefully honed
				selling system refined over the past decade, helping sellers achieve outcomes beyond
				expectations — confidently, and without financial surprises.
			</p>
		</div>
	</div>
</section>

<!-- Financial Calculations Section -->
<section class="calculations-section">
	<div class="container">
		<div class="calculations-content">
			<div class="calculations-text">
				<h2>Financial Calculations & Timeline Planning</h2>
				<p class="intro-text">We don't believe in guesswork.</p>
				<p>As part of the selling process, we perform:</p>

				<div class="calculations-list">
					{#each calculations as calc, i}
						<div class="calculation-item" class:visible={calculationsVisible} style="--delay: {i}">
							<div class="calc-icon">
								<Icon icon={calc.icon} width="28" height="28" />
							</div>
							<div class="calc-content">
								<h3>{calc.title}</h3>
								<p>{calc.description}</p>
							</div>
						</div>
					{/each}
				</div>

				<div class="highlight-box">
					<Icon icon="mdi:lightbulb-on-outline" width="24" height="24" />
					<p>
						This step alone has helped countless clients avoid bridging loans, rushed decisions, and
						moving twice.
					</p>
				</div>
			</div>

			<!-- Process Image -->
			<div class="process-image">
				<img src="/img/selling-process.jpg" alt="Step By Step of Selling Property" loading="lazy" />
				<p class="image-caption">Step By Step of Selling Property</p>
			</div>
		</div>
	</div>
</section>

<!-- Strategy Section -->
<section class="strategy-section">
	<div class="container">
		<h2 class="section-title">Our Proven Selling Strategy</h2>
		<p class="section-description">
			Over the years, we've developed and refined a comprehensive process designed to get you the
			best price, with the least stress.
		</p>

		<div class="strategy-grid">
			{#each strategies as strategy, i}
				<div class="strategy-card" class:visible={strategyVisible} style="--delay: {i}">
					<div class="strategy-icon">
						<Icon icon={strategy.icon} width="32" height="32" />
					</div>
					<h3>{strategy.title}</h3>
					<p>{strategy.description}</p>
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
				We were so worried about timing and finances... but Derrick mapped everything out — sale,
				purchase, even the cash flow. We sold above asking and moved into our new home seamlessly,
				without financial stress.
			</p>
			<p class="testimonial-author">
				<strong>Kelvin & May</strong><br />
				Sold and Upgraded to EC
			</p>
		</div>
	</div>
</section>

<!-- Benefits Section -->
<section class="benefits-section">
	<div class="container">
		<h2 class="section-title">Selling With Clarity & Confidence</h2>
		<p class="section-description">
			When you engage us, you're not just hiring agents — you're getting:
		</p>

		<div class="benefits-grid">
			{#each benefits as benefit, i}
				<div class="benefit-card" class:visible={benefitsVisible} style="--delay: {i}">
					<div class="benefit-icon">
						<Icon icon={benefit.icon} width="40" height="40" />
					</div>
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
			<h2>Ready to Sell With Strategy, Not Stress?</h2>
			<p>
				Schedule a 1-to-1 Selling Consultation with Derrick. Let's help you sell right — with strong
				marketing, smart numbers, and a clear timeline.
			</p>
			<a href="/contact" class="cta-button">Schedule My Consultation</a>
		</div>
	</div>
</section>

<style lang="scss">
	.container {
		max-width: 1135px;
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
		}
	}

	/* Financial Calculations Section */
	.calculations-section {
		padding: 80px 0;
		background: #f5f5f5;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.calculations-content {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 60px;
		align-items: start;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
			gap: 40px;
		}
	}

	.calculations-text {
		h2 {
			font-size: 32px;
			margin: 0 0 16px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 24px;
			}
		}

		.intro-text {
			font-size: 18px;
			font-weight: 600;
			color: #3a3546;
			margin: 0 0 12px 0;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		p {
			font-size: 16px;
			line-height: 1.7;
			color: #666;
			margin: 0 0 24px 0;

			@media (max-width: 768px) {
				font-size: 15px;
			}
		}
	}

	.calculations-list {
		display: flex;
		flex-direction: column;
		gap: 24px;
		margin-bottom: 32px;
	}

	.calculation-item {
		display: flex;
		gap: 16px;
		background: #fff;
		padding: 20px;
		border-radius: 12px;
		opacity: 0;
		transform: translateX(-30px);
		transition: all 0.6s ease;

		&.visible {
			opacity: 1;
			transform: translateX(0);
			transition-delay: calc(var(--delay) * 0.15s);
		}

		@media (max-width: 768px) {
			flex-direction: column;
			align-items: flex-start;
		}
	}

	.calc-icon {
		flex-shrink: 0;
		width: 48px;
		height: 48px;
		background: #3a3546;
		color: #fff;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.calc-content {
		flex: 1;

		h3 {
			font-size: 18px;
			margin: 0 0 8px 0;
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

	.highlight-box {
		display: flex;
		gap: 12px;
		align-items: flex-start;
		background: #fff;
		padding: 20px;
		border-radius: 12px;
		border-left: 4px solid #3a3546;

		:global(svg) {
			color: #3a3546;
			flex-shrink: 0;
			margin-top: 2px;
		}

		p {
			font-size: 16px;
			line-height: 1.6;
			color: #333;
			margin: 0;
			font-weight: 500;

			@media (max-width: 768px) {
				font-size: 15px;
			}
		}
	}

	.process-image {
		position: sticky;
		top: 100px;

		@media (max-width: 768px) {
			position: relative;
			top: 0;
			order: -1;
		}

		img {
			width: 100%;
			height: auto;
			border-radius: 12px;
			box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
		}

		.image-caption {
			font-size: 14px;
			color: #666;
			text-align: center;
			margin-top: 12px;
			font-style: italic;

			@media (max-width: 768px) {
				font-size: 13px;
			}
		}
	}

	:global(html[data-theme='dark']) .calculations-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .calculations-text {
		h2 {
			color: #fff;
		}

		.intro-text {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .calculation-item {
		background: #1a1a1a;
	}

	:global(html[data-theme='dark']) .calc-icon {
		background: #fff;
		color: #1a1a1a;
	}

	:global(html[data-theme='dark']) .calc-content {
		h3 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .highlight-box {
		background: #1a1a1a;
		border-left-color: #fff;

		:global(svg) {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .process-image .image-caption {
		color: #aaa;
	}

	/* Strategy Section */
	.strategy-section {
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

	.strategy-grid {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 24px;
		max-width: 1000px;
		margin: 0 auto;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
		}
	}

	.strategy-card {
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

	.strategy-icon {
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

	:global(html[data-theme='dark']) .strategy-card {
		background: #27272a;

		h3 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .strategy-icon {
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
			transition-delay: calc(var(--delay) * 0.15s);
		}

		@media (max-width: 768px) {
			padding: 24px;
		}
	}

	.benefit-icon {
		width: 64px;
		height: 64px;
		background: #3a3546;
		color: #fff;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		margin: 0 auto 16px;
	}

	.benefit-card h3 {
		font-size: 20px;
		margin: 0 0 12px 0;
		color: #333;

		@media (max-width: 768px) {
			font-size: 18px;
		}
	}

	.benefit-card p {
		font-size: 16px;
		line-height: 1.6;
		color: #666;
		margin: 0;

		@media (max-width: 768px) {
			font-size: 15px;
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

	:global(html[data-theme='dark']) .benefit-icon {
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
