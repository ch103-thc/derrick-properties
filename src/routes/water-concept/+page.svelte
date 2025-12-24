<script>
	import { onMount } from 'svelte';

	let isVisible = $state(false);
	let conceptsVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						if (entry.target.classList.contains('hero-section')) {
							isVisible = true;
						}
						if (entry.target.classList.contains('concepts-section')) {
							conceptsVisible = true;
						}
					}
				});
			},
			{ threshold: 0.1 }
		);

		const heroSection = document.querySelector('.hero-section');
		const conceptsSection = document.querySelector('.concepts-section');

		if (heroSection) observer.observe(heroSection);
		if (conceptsSection) observer.observe(conceptsSection);

		return () => observer.disconnect();
	});

	const concepts = [
		{
			letter: 'W',
			title: 'Wealth Creation',
			description:
				'The foundation of every successful property journey starts here. We focus on identifying high-potential properties — be it undervalued assets, upcoming growth areas, or favourable entry points — ensuring every purchase starts you on the right foot.',
			points: [
				'Spotting undervalued properties or areas with growth upside',
				'Leveraging on financial tools (Loan structuring, grants, tax strategies)',
				'Balancing lifestyle goals with financial prudence'
			]
		},
		{
			letter: 'A',
			title: 'Asset Progression',
			description:
				"Your Property shouldn't be static. As your financial situation improves, we guide you on how to progressively restructure or upgrade your assets — moving from HDB to private properties, or rebalancing your portfolio to increase returns. Even upgrading the size of your HDB helps in this aspect.",
			points: [
				'Timing HDB upgrades to another HDB, ECs or Private Condos',
				'Smart reinvestment strategies (Decoupling, right-sizing, or further leveraging)',
				'Avoiding Over-leverage and excessive debt traps (securing a safety net over your next purchase)'
			]
		},
		{
			letter: 'T',
			title: 'Timing the Market',
			description:
				'While nobody can predict the market perfectly, we believed in making decision based on data, trends, and calculated timing. With over a decade of experience and a keen eye for market statistics, we help you:',
			points: [
				'Understand property cycle and price movements',
				'Know when to hold, sell or buy',
				'Avoid emotional decisions and speculative risks'
			]
		},
		{
			letter: 'E',
			title: 'Exit Strategy',
			description:
				'A sound property plan includes knowing how, and when to exit, including understand the trends to determine a safe entry price to ensure a sound exit strategies. The cheapest property might not have a good exit plan while the most expensive property might give you a safe exit strategy. This is made possible with a full understand of the property market, masterplan as well as transformation stages.'
		},
		{
			letter: 'R',
			title: 'Retirement Ready',
			description:
				'The ultimate goal of the W.A.T.E.R Concept is simple: Enable you to retire early, comfortably, and securely. Through careful planning and step-by-step wealth accumulation, your property portfolio should eventually generate sustainable passive income or equity you can tap into — giving you financial freedom without stress.'
		}
	];

	const benefits = [
		{
			title: 'Tailored for Individuals',
			description: 'We understand your financial goals, life plans, and even family needs'
		},
		{
			title: 'Risk-mitigation focused',
			description: 'Every step is built to minimise risks while maximising returns'
		},
		{
			title: 'Proven Track Records',
			description:
				'Over 50+ Clients have successfully implemented this framework, moving closer to their retirement goals'
		}
	];
</script>

<svelte:head>
	<title>W.A.T.E.R Concept - Wealth Accumulation Towards Early Retirement</title>
	<meta
		name="description"
		content="Discover the W.A.T.E.R Concept - A systematic framework for wealth accumulation through property investments, designed for early retirement."
	/>
</svelte:head>

<!-- Hero Section -->
<section class="hero-section" class:visible={isVisible}>
	<div class="container">
		<div class="hero-content">
			<h1>W.A.T.E.R Concept</h1>
			<p class="hero-subtitle">Wealth Accumulation Towards Early Retirement</p>
			<p class="hero-description">
				Derrick believes that property should be more than just a home — it should be a tool
				for wealth-building, financial security, and ultimately, early retirement.
			</p>
		</div>
	</div>
</section>

<!-- Introduction Section -->
<section class="intro-section">
	<div class="container">
		<div class="intro-content">
			<p>
				Over the years, we notice one common challenge faced by many couples: They focus on the
				next property move without a clear, long-term strategy, often missing key opportunities to
				grow their net worth.
			</p>
			<p>
				That's why we developed the <strong>W.A.T.E.R concept</strong> — Wealth Accumulation Towards
				Early Retirement. This Signature framework is designed specifically for couples, providing a
				step-by-step approached to accumulate wealth systematically through property investments, all
				while minimising risks and planning ahead for sustainable retirement.
			</p>
		</div>
	</div>
</section>

<!-- Concepts Section -->
<section class="concepts-section">
	<div class="container">
		<h2 class="section-title">Breaking Down the W.A.T.E.R Concept</h2>

		<div class="concepts-grid">
			{#each concepts as concept, i}
				<div class="concept-card" class:visible={conceptsVisible} style="--delay: {i}">
					<div class="concept-header">
						<div class="concept-letter">{concept.letter}</div>
						<h3>{concept.title}</h3>
					</div>
					<p class="concept-description">{concept.description}</p>
					{#if concept.points}
						<ul class="concept-points">
							{#each concept.points as point}
								<li>{point}</li>
							{/each}
						</ul>
					{/if}
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Why Trust Section -->
<section class="trust-section">
	<div class="container">
		<h2 class="section-title">Why Clients Trust Our W.A.T.E.R Concept</h2>

		<div class="benefits-grid">
			{#each benefits as benefit}
				<div class="benefit-card">
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
			<h2>Start Building Your Future Today</h2>
			<p>
				Property decisions aren't just about the now — they're about your long-term freedom.
			</p>
			<p>
				Before you make your next move, let's sit down and map out your personalised W.A.T.E.R
				Concept.
			</p>
			<p class="cta-note">
				No pressure, no obligation — just clear, data-backed advice focused entirely on your goals.
			</p>
			<a href="/contact" class="cta-button">Schedule a Consultation</a>
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
		max-width: 800px;
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
			color: #666;
			font-weight: 500;

			@media (max-width: 768px) {
				font-size: 18px;
			}
		}

		.hero-description {
			font-size: 18px;
			line-height: 1.7;
			color: #666;
			margin: 0;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}
	}

	:global(html[data-theme='dark']) .hero-content {
		h1 {
			color: #fff;
		}

		.hero-subtitle,
		.hero-description {
			color: #aaa;
		}
	}

	/* Introduction Section */
	.intro-section {
		padding: 60px 0;
		background: #f5f5f5;

		@media (max-width: 768px) {
			padding: 40px 0;
		}
	}

	.intro-content {
		max-width: 900px;
		margin: 0 auto;

		p {
			font-size: 18px;
			line-height: 1.8;
			color: #333;
			margin: 0 0 24px 0;

			&:last-child {
				margin-bottom: 0;
			}

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		strong {
			color: #3a3546;
			font-weight: 600;
		}
	}

	:global(html[data-theme='dark']) .intro-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .intro-content {
		p {
			color: #aaa;
		}

		strong {
			color: #fff;
		}
	}

	/* Concepts Section */
	.concepts-section {
		padding: 80px 0;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.section-title {
		font-size: 32px;
		text-align: center;
		margin: 0 0 48px 0;
		color: #333;

		@media (max-width: 768px) {
			font-size: 24px;
			margin: 0 0 32px 0;
		}
	}

	:global(html[data-theme='dark']) .section-title {
		color: #fff;
	}

	.concepts-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 32px;
		max-width: 900px;
		margin: 0 auto;

		@media (max-width: 768px) {
			gap: 24px;
		}
	}

	.concept-card {
		background: #f5f5f5;
		border-radius: 12px;
		padding: 32px;
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

	.concept-header {
		display: flex;
		align-items: center;
		gap: 16px;
		margin-bottom: 16px;
	}

	.concept-letter {
		width: 48px;
		height: 48px;
		background: #3a3546;
		color: #fff;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 24px;
		font-weight: 700;
		flex-shrink: 0;
	}

	.concept-header h3 {
		font-size: 24px;
		margin: 0;
		color: #333;

		@media (max-width: 768px) {
			font-size: 20px;
		}
	}

	.concept-description {
		font-size: 16px;
		line-height: 1.7;
		color: #666;
		margin: 0 0 16px 0;

		@media (max-width: 768px) {
			font-size: 15px;
		}
	}

	.concept-points {
		list-style: none;
		padding: 0;
		margin: 0;

		li {
			font-size: 16px;
			line-height: 1.6;
			color: #666;
			padding-left: 24px;
			position: relative;
			margin-bottom: 12px;

			&:before {
				content: '•';
				position: absolute;
				left: 8px;
				color: #3a3546;
				font-weight: 700;
			}

			&:last-child {
				margin-bottom: 0;
			}

			@media (max-width: 768px) {
				font-size: 15px;
			}
		}
	}

	:global(html[data-theme='dark']) .concept-card {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .concept-letter {
		background: #fff;
		color: #1a1a1a;
	}

	:global(html[data-theme='dark']) .concept-header h3 {
		color: #fff;
	}

	:global(html[data-theme='dark']) .concept-description,
	:global(html[data-theme='dark']) .concept-points li {
		color: #aaa;
	}

	:global(html[data-theme='dark']) .concept-points li:before {
		color: #fff;
	}

	/* Trust Section */
	.trust-section {
		padding: 80px 0;
		background: #f5f5f5;

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
		background: #fff;
		border-radius: 12px;
		padding: 32px;
		text-align: center;

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

	:global(html[data-theme='dark']) .trust-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .benefit-card {
		background: #1a1a1a;

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
			margin: 0 0 16px 0;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.cta-note {
			font-style: italic;
			margin-bottom: 32px;
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