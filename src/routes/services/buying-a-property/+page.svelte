<script>
	import { onMount } from 'svelte';
	import Icon from '@iconify/svelte';

	let isVisible = $state(false);
	let approachVisible = $state(false);
	let processVisible = $state(false);
	let empowermentVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						if (entry.target.classList.contains('hero-section')) {
							isVisible = true;
						}
						if (entry.target.classList.contains('approach-section')) {
							approachVisible = true;
						}
						if (entry.target.classList.contains('process-section')) {
							processVisible = true;
						}
						if (entry.target.classList.contains('empowerment-section')) {
							empowermentVisible = true;
						}
					}
				});
			},
			{ threshold: 0.1 }
		);

		const heroSection = document.querySelector('.hero-section');
		const approachSection = document.querySelector('.approach-section');
		const processSection = document.querySelector('.process-section');
		const empowermentSection = document.querySelector('.empowerment-section');

		if (heroSection) observer.observe(heroSection);
		if (approachSection) observer.observe(approachSection);
		if (processSection) observer.observe(processSection);
		if (empowermentSection) observer.observe(empowermentSection);

		return () => observer.disconnect();
	});

	const approaches = [
		{
			icon: 'mdi:shield-check',
			title: 'Safe Entry Prices',
			description:
				"We analyse past transactions, area trends, and growth patterns to ensure you're not overpaying — especially in high-competition markets."
		},
		{
			icon: 'mdi:map-marker-radius',
			title: 'Location Transformation Potential',
			description:
				'We help you identify upcoming growth zones with URA transformation plans, MRT developments, and new amenities.'
		},
		{
			icon: 'mdi:exit-run',
			title: 'Exit Strategy',
			description:
				'We think ahead before you buy — who will your future buyer be, and how will this property serve your long-term goals.'
		}
	];

	const processSteps = [
		{
			icon: 'mdi:calculator-variant',
			title: 'Financial Calculation & Affordability Analysis',
			description:
				'We assess your budget, CPF, loan eligibility, and cash-on-hand — ensuring you know exactly what you can afford before viewing a single unit.'
		},
		{
			icon: 'mdi:timeline-clock-outline',
			title: 'Timeline Planning',
			description:
				'We sync your buying journey with your personal life milestones, family needs, or property sale (if upgrading) — helping you avoid rushed decisions, double housing payments, or missed windows.'
		},
		{
			icon: 'mdi:currency-usd',
			title: 'Safe Entry Price Guidance',
			description:
				"We analyse past transactions, area trends, and growth patterns to ensure you're not overpaying — especially in high-competition markets. Every recommendation we make is supported by hard numbers, not hype."
		},
		{
			icon: 'mdi:chart-line-variant',
			title: 'Transformation & Location Insights',
			description:
				'We help you identify upcoming growth zones — areas with URA transformation plans, MRT developments, new amenities or school upgrades. This foresight positions you to enjoy capital appreciation in the years ahead.'
		},
		{
			icon: 'mdi:strategy',
			title: 'Exit Strategy Planning',
			description:
				'Before you buy, we already think ahead: Who will your future buyer be? What will your holding period look like? Will this be your final home or an investment stepping stone? We ensure your purchase is not a trap, but a tool — for future upgrading, passive income, or early retirement.'
		}
	];

	const empowermentPoints = [
		{
			icon: 'mdi:check-circle',
			text: 'Clarity with numbers'
		},
		{
			icon: 'mdi:check-circle',
			text: 'Confidence with planning'
		},
		{
			icon: 'mdi:check-circle',
			text: 'Calmness with expert guidance'
		}
	];
</script>

<svelte:head>
	<title>Buying a Property - Strategic Guidance | D'Home Series</title>
	<meta
		name="description"
		content="Buy with strategy, clarity, and confidence. Personalized support to find the right home or investment property with safe entry prices and exit strategies."
	/>
</svelte:head>

<!-- Hero Section -->
<section class="hero-section" class:visible={isVisible}>
	<div class="container">
		<div class="hero-content">
			<h1>Buying a Property</h1>
			<p class="hero-subtitle">
				Don't Just Buy A Home. Buy With Strategy, Clarity, and Confidence.
			</p>
			<p class="hero-description">
				Buying a property is one of life's biggest decisions — and also one of the most stressful.
			</p>
			<p class="hero-description">
				Between affordability calculations, conflicting advice, and overwhelming choices, it's easy
				to get lost. But you don't have to navigate it alone.
			</p>
			<p class="hero-description">
				At D'Home Series, we simplify and de-stress your property journey through a refined process,
				built on over a decade of real-life experience, grounded in data, and focused on your
				long-term success.
			</p>
		</div>
	</div>
</section>

<!-- What Makes Different Section -->
<section class="approach-section">
	<div class="container">
		<h2 class="section-title">What Makes Our Approach Different?</h2>
		<p class="section-description">
			We don't just help you "buy a home." We guide you to make a smart, strategic move by looking
			beyond surface appeal — to Safe Entry Prices, Location Transformation Potential, and a clear
			Exit Strategy.
		</p>

		<div class="approach-grid">
			{#each approaches as approach, i}
				<div class="approach-card" class:visible={approachVisible} style="--delay: {i}">
					<div class="approach-icon">
						<Icon icon={approach.icon} width="40" height="40" />
					</div>
					<h3>{approach.title}</h3>
					<p>{approach.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Empowerment Section -->
<section class="empowerment-section">
	<div class="container">
		<div class="empowerment-content">
			<h2>Buying is Stressful. We Make It Empowering.</h2>
			<p>We know property buying comes with pressure. That's why we provide:</p>

			<div class="empowerment-list">
				{#each empowermentPoints as point, i}
					<div class="empowerment-item" class:visible={empowermentVisible} style="--delay: {i}">
						<Icon icon={point.icon} width="24" height="24" />
						<span>{point.text}</span>
					</div>
				{/each}
			</div>

			<p class="empowerment-note">
				Every decision is backed by stats, timelines, and projected scenarios — so you move forward
				without second-guessing.
			</p>
		</div>
	</div>
</section>

<!-- Process Section -->
<section class="process-section">
	<div class="container">
		<h2 class="section-title">Our Proven Buying Process</h2>

		<div class="process-content">
			<div class="process-list">
				{#each processSteps as step, i}
					<div class="process-card" class:visible={processVisible} style="--delay: {i}">
						<div class="process-icon">
							<Icon icon={step.icon} width="32" height="32" />
						</div>
						<div class="process-text">
							<h3>{step.title}</h3>
							<p>{step.description}</p>
						</div>
					</div>
				{/each}
			</div>

			<!-- Process Image -->
			<div class="process-image">
				<img src="/img/buying-process.jpg" alt="Buying a Property Process" loading="lazy" />
				<p class="image-caption">Our Step-by-Step Buying Process</p>
			</div>
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
				Derrick showed us options we never even considered — and helped us buy below market value in
				an area with upcoming transformation. Their breakdown of timeline and costs gave us total
				peace of mind.
			</p>
			<p class="testimonial-author">
				<strong>Jia Hui & Brandon</strong><br />
				First-Time Condo Buyers
			</p>
		</div>
	</div>
</section>

<!-- Call to Action Section -->
<section class="journey-section">
	<div class="container">
		<div class="journey-content">
			<h2>Don't Embark on This Journey Alone</h2>
			<p>
				Whether you're buying your first home, upgrading, or adding to your investment portfolio —
				you need someone who knows the landscape inside out.
			</p>

			<div class="journey-points">
				<p>
					<Icon icon="mdi:arrow-right" width="20" height="20" /> You need more than a property agent.
				</p>
				<p>
					<Icon icon="mdi:arrow-right" width="20" height="20" /> You need a strategist who's walked this
					path hundreds of times.
				</p>
				<p><Icon icon="mdi:arrow-right" width="20" height="20" /> You need Derrick.</p>
			</div>
		</div>
	</div>
</section>

<!-- CTA Section -->
<section class="cta-section">
	<div class="container">
		<div class="cta-content">
			<h2>Ready to Buy Smarter?</h2>
			<p>
				Book your 1-to-1 Buying Consultation today. We'll walk you through the numbers, the areas,
				the risks, and the right steps — so your next move brings you closer to your life goals.
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

	/* Approach Section */
	.approach-section {
		padding: 80px 0;
		background: #f5f5f5;

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

	.approach-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 24px;
		max-width: 1100px;
		margin: 0 auto;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
		}
	}

	.approach-card {
		background: #fff;
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

	.approach-icon {
		width: 72px;
		height: 72px;
		background: #3a3546;
		color: #fff;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		margin: 0 auto 20px;
	}

	.approach-card h3 {
		font-size: 20px;
		margin: 0 0 12px 0;
		color: #333;

		@media (max-width: 768px) {
			font-size: 18px;
		}
	}

	.approach-card p {
		font-size: 16px;
		line-height: 1.6;
		color: #666;
		margin: 0;

		@media (max-width: 768px) {
			font-size: 15px;
		}
	}

	:global(html[data-theme='dark']) .approach-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .approach-card {
		background: #1a1a1a;

		h3 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .approach-icon {
		background: #fff;
		color: #1a1a1a;
	}

	/* Empowerment Section */
	.empowerment-section {
		padding: 80px 0;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.empowerment-content {
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

		> p {
			font-size: 18px;
			color: #666;
			margin: 0 0 32px 0;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.empowerment-note {
			font-size: 16px;
			color: #3a3546;
			font-weight: 600;
			margin-top: 32px;

			@media (max-width: 768px) {
				font-size: 15px;
			}
		}
	}

	.empowerment-list {
		display: flex;
		flex-direction: column;
		gap: 16px;
		max-width: 500px;
		margin: 0 auto;
	}

	.empowerment-item {
		display: flex;
		align-items: center;
		gap: 12px;
		padding: 16px 24px;
		background: #f5f5f5;
		border-radius: 12px;
		opacity: 0;
		transform: translateX(-30px);
		transition: all 0.6s ease;

		&.visible {
			opacity: 1;
			transform: translateX(0);
			transition-delay: calc(var(--delay) * 0.15s);
		}

		:global(svg) {
			color: #3a3546;
			flex-shrink: 0;
		}

		span {
			font-size: 18px;
			color: #333;
			font-weight: 500;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}
	}

	:global(html[data-theme='dark']) .empowerment-content {
		h2 {
			color: #fff;
		}

		> p {
			color: #aaa;
		}

		.empowerment-note {
			color: #fff;
		}
	}

	:global(html[data-theme='dark']) .empowerment-item {
		background: #27272a;

		:global(svg) {
			color: #fff;
		}

		span {
			color: #fff;
		}
	}

	/* Process Section */
	.process-section {
		padding: 80px 0;
		background: #f5f5f5;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.process-content {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 60px;
		align-items: start;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
			gap: 40px;
		}
	}

	.process-list {
		display: flex;
		flex-direction: column;
		gap: 24px;
	}

	.process-card {
		display: flex;
		gap: 20px;
		background: #fff;
		padding: 24px;
		border-radius: 12px;
		opacity: 0;
		transform: translateX(-30px);
		transition: all 0.6s ease;

		&.visible {
			opacity: 1;
			transform: translateX(0);
			transition-delay: calc(var(--delay) * 0.1s);
		}

		@media (max-width: 768px) {
			flex-direction: column;
		}
	}

	.process-icon {
		flex-shrink: 0;
		width: 56px;
		height: 56px;
		background: #3a3546;
		color: #fff;
		border-radius: 12px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.process-text {
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

	:global(html[data-theme='dark']) .process-section {
		background: #27272a;
	}

	:global(html[data-theme='dark']) .process-card {
		background: #1a1a1a;
	}

	:global(html[data-theme='dark']) .process-icon {
		background: #fff;
		color: #1a1a1a;
	}

	:global(html[data-theme='dark']) .process-text {
		h3 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .process-image .image-caption {
		color: #aaa;
	}

	/* Testimonial Section */
	.testimonial-section {
		padding: 80px 0;

		@media (max-width: 768px) {
			padding: 60px 0;
		}
	}

	.testimonial-card {
		max-width: 900px;
		margin: 0 auto;
		background: #f5f5f5;
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

	:global(html[data-theme='dark']) .testimonial-card {
		background: #27272a;
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
			margin: 0 0 24px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 24px;
			}
		}

		> p {
			font-size: 18px;
			line-height: 1.7;
			color: #666;
			margin: 0 0 32px 0;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}
	}

	.journey-points {
		display: flex;
		flex-direction: column;
		gap: 16px;
		max-width: 600px;
		margin: 0 auto;

		p {
			display: flex;
			align-items: center;
			justify-content: center;
			gap: 12px;
			font-size: 18px;
			color: #333;
			margin: 0;
			font-weight: 500;

			@media (max-width: 768px) {
				font-size: 16px;
				justify-content: flex-start;
			}

			:global(svg) {
				color: #3a3546;
				flex-shrink: 0;
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

		> p {
			color: #aaa;
		}
	}

	:global(html[data-theme='dark']) .journey-points p {
		color: #fff;

		:global(svg) {
			color: #fff;
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
