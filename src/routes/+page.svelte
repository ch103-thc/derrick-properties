<script>
	import Icon from '@iconify/svelte';

	const services = [
		{
			image: 'img/service/retirement.jpg',
			title: 'Planning for Retirement',
			description:
				'Strategic real estate planning to help you build long-term security and a stable retirement income.'
		},
		{
			image: 'img/service/consulting.jpg',
			title: 'Real Estate Consulting',
			description:
				'Expert consultation for buying, selling, investing, and renting for passive income in real estate markets.'
		},
		{
			image: 'img/service/restructuring.png',
			title: 'Asset Restructuring',
			description:
				'Optimise your property portfolio through restructuring strategies that enhance long-term financial growth.'
		},
		{
			image: 'img/service/selling.jpeg',
			title: 'Selling a Property',
			description:
				'Comprehensive guidance to position, market, and sell your property at the best possible price.'
		},
		{
			image: 'img/service/buying.jpeg',
			title: 'Buying a Property',
			description:
				'Personalised support to help you find the right home or investment property that fits your goals.'
		},
		{
			image: 'img/service/renting.jpeg',
			title: 'Renting a Property',
			description:
				'Assistance in renting out or finding rental properties with ease and confidence.'
		}
	];

	// const journeys = [
	// 	{
	// 		review:
	// 			'Working with this team made buying our first home a breeze. Their expertise and dedication exceeded our expectations.',
	// 		name: 'Sarah Johnson'
	// 	},
	// 	{
	// 		review:
	// 			'Professional, knowledgeable, and always available. They helped us find the perfect property for our business.',
	// 		name: 'Michael Chen'
	// 	},
	// 	{
	// 		review:
	// 			'Outstanding service from start to finish. They truly understand the market and their clients needs.',
	// 		name: 'Emily Rodriguez'
	// 	}
	// ];

	const journeys = [
		{
			review: [
				'Emilia first connected with me through Facebook, and we soon met up for a chat. She shared several concerns — whether she could afford a home on a single income, how to manage her monthly mortgage as a nurse, and the importance of living close to her sister so her nephews and nieces could still visit their grandpa regularly.',
				'Together, we explored different possibilities and worked out what was financially and practically achievable. Once we set our plan in motion, the search began — though not without its challenges. Emilia faced additional hurdles, including her father’s outstanding town council payments and other unsettled dues from a previous rental flat, all while balancing her demanding work schedule.',
				'Despite the ups and downs, we eventually found a home that checked all her boxes — a high-floor unit right next to her children’s school. The seller even agreed to a lower option fee, which made the deal possible. It was truly fulfilling to see everything come together and help Emilia secure a home that perfectly fits her family’s needs.'
			],
			name: "Emilia's Story",
			photo: 'img/journey/emilia-story.jpg'
		},
		{
			review: [
				'Gloria was introduced to me through a friend’s wife. During our consultation, I learned that she had recently obtained her Singapore citizenship and was eager to own her first home here — a place where she could also host her parents when they visit from her hometown in the future.',
				'Her main concern was not having enough CPF savings to cover the downpayment while still wanting to set aside sufficient cash for renovation expenses. After careful planning and discussion, we managed to secure a home near an LRT station — offering her both convenience to work and financial comfort within her budget.',
				'The best part? She was able to move in earlier than expected, without having to wait long after completion. It was a joy to see everything fall into place for Gloria as she began this new chapter in her own home.'
			],
			name: "Gloria's Story",
			photo: 'img/journey/gloria-story.jpg'
		},
		{
			review: [
				'When Raymond and Faye first connected with me, they just wanted to understand how an Executive Condo (EC) works. They were sceptical at first — worried about whether upgrading would stretch their finances too much and if it might affect their family’s lifestyle. With two lovely daughters still in school, they didn’t want to risk their family’s comfort or future plans.',
				'During our chat, I walked them through my W.A.T.E.R. Concept and L.E.X. Framework, which helped them see their situation with fresh clarity. Step by step, they realised that upgrading to an EC wasn’t as out of reach as they once thought.',
				'In the end, they decided to secure a home at OLA, one that truly fits their family’s needs — now and in the years ahead. What touched me most was seeing how their worries turned into excitement once they had a clear plan in place.',
				'With their decision made, they now have peace of mind (and time!) to grow their savings before key collection. I’m really proud of them for opening their minds and taking this confident step toward their family’s future. 🌟'
			],
			name: "Raymond and Faye's Story",
			photo: 'img/journey/raymond-faye-story.jpg'
		}
	];

	const reads = [
		{
			image: 'img/read/first.jpg',
			date: 'Nov 5, 2025',
			title: 'Understand Property Market Trends in 2025',
			description:
				'Key insights into the evolving real estate landscape and what it means for investors and homeowners.'
		},
		{
			image: 'img/read/second.jpg',
			date: 'Oct 28, 2025',
			title: 'Portfolio Upgrading: A Strategic Approach',
			description:
				'Learn how to systematically upgrade your property portfolio for long-term wealth growth.'
		},
		{
			image: 'img/read/third.jpg',
			date: 'Oct 15, 2025',
			title: 'Overseas Property Investment Guide',
			description:
				'Essential considerations when evaluating international real estate opportunities.'
		}
	];

	import { onMount } from 'svelte';

	// Add after your existing state variables
	let servicesVisible = $state(false);
	let journeysVisible = $state(false);
	let readsVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						if (entry.target.classList.contains('services')) {
							servicesVisible = true;
						}
						if (entry.target.classList.contains('journeys')) {
							journeysVisible = true;
						}
						if (entry.target.classList.contains('reads')) {
							readsVisible = true;
						}
					}
				});
			},
			{ threshold: 0.1 }
		);

		const servicesSection = document.querySelector('.services');
		const journeysSection = document.querySelector('.journeys');
		const readsSection = document.querySelector('.reads');

		if (servicesSection) observer.observe(servicesSection);
		if (journeysSection) observer.observe(journeysSection);
		if (readsSection) observer.observe(readsSection);

		return () => observer.disconnect();
	});
</script>

<!-- About/Info Section -->
<section class="info-section">
	<div class="container">
		<div class="info-content">
			<div class="info-text">
				<h2>About Me</h2>
				<p>
					I'm Derrick Teo, a former Sales Manager in the engineering industry, whom brings along a
					systematic and data-driven approach to real estate — where precision meets people.
					Specialising in portfolio upgrading, I help clients make informed decisions that align
					with their long-term financial goals.
				</p>
				<p>
					Known for my clarity and integrity, I go beyond surface-level advice, offering insights
					into options, risks, and opportunities. My analytical yet practical guidance empowers
					homeowners and investors to act with confidence.
				</p>
				<p>
					Whether you’re upgrading, restructuring your portfolio, evaluating overseas assets, or
					planning for retirement, I ensure every move is intentional, calculated and part of a
					sustainable roadmap towards wealth growth.
				</p>
				<p>
					I’m approachable, genuine, and always happy to chat about how I can be part of your plan
					for your next move with purpose.
				</p>
				<a href="/contact" class="cta-button">Let's Chat</a>
			</div>
			<div class="info-image-wrapper">
				<div class="info-image">
					<img src="img/profile.jpg" alt="Derrick Teo" />
				</div>
			</div>
		</div>
	</div>
</section>

<!-- Services Section -->
<section class="services">
	<div class="container">
		<div class="section-title" class:visible={servicesVisible}>
			<h2>How can we help you?</h2>
			<p class="sub-header">Comprehensive real estate services tailored to your needs</p>
		</div>

		<div class="services-grid">
			{#each services as service, i}
				<div class="service-card" class:visible={servicesVisible} style="--delay: {i}">
					<div class="service-image">
						<img src={service.image} alt={service.title} loading="lazy" />
					</div>
					<div class="service-info">
						<h3>{service.title}</h3>
						<p>{service.description}</p>
						<a href="/services/{service.title}" class="read-more">Read More</a>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Journeys Section -->
<section class="journeys">
	<div class="container">
		<div class="section-title" class:visible={journeysVisible}>
			<h2>My Customer's Journey With Me</h2>
		</div>

		<div class="journeys-grid">
			{#each journeys as journey, i}
				<div class="journey-card" class:visible={journeysVisible} style="--delay: {i}">
					<div class="journey-image">
						<img src={journey.photo} alt={journey.name} loading="lazy" />
					</div>
					<div class="journey-info">
						<h3>{journey.name}</h3>
						<div class="journey-text">
							{#each journey.review as paragraph}
								<p>{paragraph}</p>
							{/each}
						</div>
						<a href="/journeys/{journey.name}" class="read-full-story">Read Full Story</a>
					</div>
				</div>
			{/each}
		</div>
		<div class="view-all">
			<a href="/journeys" class="view-all-btn">View All Stories</a>
		</div>
	</div>
</section>

<!-- Featured Reads Section -->
<section class="reads">
	<div class="container">
		<div class="section-title" class:visible={readsVisible}>
			<h2>Featured Reads</h2>
			<p class="sub-header">Insights and updates from the real estate world</p>
		</div>

		<div class="reads-grid">
			{#each reads as read, i}
				<article class="read-card" class:visible={readsVisible} style="--delay: {i}">
					<div class="read-image">
						<img src={read.image} alt={read.title} />
					</div>
					<div class="read-content">
						<h3>{read.title}</h3>
						<p class="read-date">{read.date}</p>
						<p class="read-description">{read.description}</p>
					</div>
				</article>
			{/each}
		</div>

		<div class="view-all">
			<a href="/reads" class="view-all-btn">View All Reads</a>
		</div>
	</div>
</section>

<style lang="scss">
	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 20px;
	}

	/* Info Section Styles */
	.info-section {
		padding: 60px 0 60px;
	}

	.info-content {
		display: grid;
		grid-template-columns: 55% 1fr;
		gap: 60px;
		align-items: center;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
			gap: 40px;
		}
	}

	.info-text {
		h2 {
			font-size: 32px;
			margin: 0 0 24px 0;
			color: #333;

			@media (max-width: 768px) {
				font-size: 1.5rem;
			}
		}

		p {
			font-size: 1rem;
			line-height: 1.7;
			margin: 0 0 20px 0;
			max-width: 590px;

			&:last-child {
				margin-bottom: 0;
			}
		}
	}

	.cta-button {
		display: inline-block;
		padding: 14px 28px;
		background: #3a3546;
		color: #f8f8f8;
		border-radius: 50px;
		font-weight: 600;
		font-size: 1rem;
		text-decoration: none;
		cursor: pointer;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
		// letter-spacing: 0.5px;
		margin-top: 16px;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
				background: #333;
			}
		}
	}

	.view-all-btn {
		display: inline-block;
		padding: 12px 20px;
		background: #3a3546;
		color: #f8f8f8;
		border-radius: 50px;
		font-weight: 600;
		font-size: 0.9rem;
		text-decoration: none;
		cursor: pointer;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
		// letter-spacing: 0.5px;
		margin-top: 0;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
				background: #333;
			}
		}
	}

	:global(html[data-theme='dark']) .cta-button,
	:global(html[data-theme='dark']) .view-all-btn {
		background: #f8f8f8;
		color: #1a1a1a;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
				background: #e0e0e0;
			}
		}
	}

	:global(html[data-theme='dark']) .info-text {
		h2 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	.info-image-wrapper {
		position: relative;
		width: 100%;

		@media (max-width: 768px) {
			order: -1;
		}
	}

	.info-image {
		position: relative;
		width: 100%;
		height: 500px;
		border-radius: 1rem;
		overflow: hidden;
		box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
		z-index: 2;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
		}
	}

	/* Services Styles */
	.services {
		padding: 100px 0 80px;
		background: #fff;

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	.section-title {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.6s ease;
		text-align: center;
		margin-bottom: 2.5rem;

		&.visible {
			opacity: 1;
			transform: translateY(0);
		}

		h2 {
			font-size: 32px;
			margin: 0 0 12px 0;
			transition-delay: 0.1s;

			@media (max-width: 768px) {
				font-size: 1.5rem;
			}
		}

		.sub-header {
			font-size: 16px;
			color: #666;
			margin: 0;
			transition-delay: 0.2s;

			@media (max-width: 768px) {
				font-size: 15px;
			}
		}
	}

	:global(html[data-theme='dark']) .section-title {
		h2 {
			color: #fff;
		}

		.sub-header {
			color: #aaa;
		}
	}

	.services-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 16px;
		margin-top: 2.5rem;

		@media (max-width: 1024px) {
			grid-template-columns: repeat(2, 1fr);
		}

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
		}
	}

	.service-card {
		position: relative;
		border-radius: 1rem;
		overflow: visible;
		height: auto;
		box-shadow: none;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		cursor: pointer;
		display: flex;
		flex-direction: column;
		background: #f5f5f5;
		padding: 16px;
		opacity: 0;
		transform: translateY(30px);

		&.visible {
			opacity: 1;
			transform: translateY(0);
			transition-delay: calc(var(--delay) * 0.1s);
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);
			}
		}
	}

	.service-image {
		width: 100%;
		height: 240px;
		overflow: hidden;
		flex-shrink: 0;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			border-radius: 1rem;
			transition: transform 0.4s ease;
		}
	}

	.service-info {
		position: relative;
		padding: 16px 0;
		background: transparent;
		color: inherit;
		flex-grow: 1;
		display: flex;
		flex-direction: column;

		@media (max-width: 768px) {
			padding: 16px 0;
		}

		h3 {
			font-size: 18px;
			margin: 0 0 8px 0;
			color: #1a1a1a;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		p {
			font-size: 15px;
			margin: 0;
			opacity: 1;
			line-height: 1.5;
			color: #666;
			flex-grow: 1;

			@media (max-width: 768px) {
				font-size: 14px;
			}
		}

		.read-more {
			display: inline-block;
			margin-top: 8px;
			font-weight: 600;
			font-size: 0.9rem;
			color: #1a1a1a;
			text-decoration: underline;
			cursor: pointer;
			transition: color 0.3s ease;

			@media (hover: hover) and (pointer: fine) {
				&:hover {
					color: #333;
				}
			}

			:global(html[data-theme='dark']) & {
				color: #fff;

				&:hover {
					color: #ddd;
				}
			}
		}
	}

	:global(html[data-theme='dark']) .service-card {
		background: #27272a;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);
			}
		}
	}

	:global(html[data-theme='dark']) .services {
		background: #1a1a1a;
	}

	:global(html[data-theme='dark']) .service-info {
		h3 {
			color: #fff;
		}

		p {
			color: #aaa;
		}
	}

	/* Journeys Styles */
	.journeys {
		padding: 100px 0 80px;

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	.journey-content {
		margin-top: 0;
	}

	.journeys-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 16px;

		@media (max-width: 1024px) {
			grid-template-columns: repeat(2, 1fr);
		}

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
		}
	}

	.journey-card {
		position: relative;
		border-radius: 1rem;
		overflow: visible;
		height: auto;
		box-shadow: none;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		cursor: pointer;
		display: flex;
		flex-direction: column;
		background: #f5f5f5;
		padding: 16px;
		opacity: 0;
		transform: translateY(30px);

		&.visible {
			opacity: 1;
			transform: translateY(0);
			transition-delay: calc(var(--delay) * 0.1s);
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);
			}
		}
	}

	.journey-image {
		width: 100%;
		height: 240px;
		overflow: hidden;
		flex-shrink: 0;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			border-radius: 1rem;
			transition: transform 0.4s ease;
		}
	}

	.journey-info {
		position: relative;
		padding: 16px 0;
		background: transparent;
		color: inherit;
		flex-grow: 1;
		display: flex;
		flex-direction: column;

		@media (max-width: 768px) {
			padding: 16px 0;
		}

		h3 {
			font-size: 18px;
			margin: 0 0 8px 0;
			color: #1a1a1a;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.read-full-story {
			display: inline-block;
			margin-top: 8px;
			font-weight: 600;
			font-size: 0.9rem;
			color: #1a1a1a;
			text-decoration: underline;
			cursor: pointer;
			transition: color 0.3s ease;

			@media (hover: hover) and (pointer: fine) {
				&:hover {
					color: #333;
				}
			}

			:global(html[data-theme='dark']) & {
				color: #fff;

				&:hover {
					color: #ddd;
				}
			}
		}
	}

	.journey-text {
		font-size: 15px;
		line-height: 1.5;
		color: #666;
		flex-grow: 1;

		display: -webkit-box;
		-webkit-line-clamp: 3;
		-webkit-box-orient: vertical;
		overflow: hidden;
		text-overflow: ellipsis;

		@media (max-width: 768px) {
			font-size: 14px;
			-webkit-line-clamp: 2;
		}

		p {
			margin: 0;
			display: inline;

			&:not(:last-child)::after {
				content: ' ';
			}
		}
	}

	:global(html[data-theme='dark']) .journey-card {
		background: #27272a;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);
			}
		}
	}

	:global(html[data-theme='dark']) .journey-info {
		h3 {
			color: #fff;
		}
	}

	:global(html[data-theme='dark']) .journey-text {
		color: #aaa;
	}

	:global(html[data-theme='dark']) .journeys-header .header-text h2 {
		color: #fff;
	}

	:global(html[data-theme='dark']) .review-wrapper {
		&::-webkit-scrollbar-track {
			background: #222;
		}

		&::-webkit-scrollbar-thumb {
			background: #555;

			&:hover {
				background: #777;
			}
		}
	}

	:global(html[data-theme='dark']) .review,
	:global(html[data-theme='dark']) .reviewer {
		color: #aaa;
	}

	/* Reads Styles */
	.reads {
		padding: 100px 0 80px;
		background: #fff;

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	:global(html[data-theme='dark']) .reads {
		background: #1a1a1a;
	}

	.reads-header {
		display: flex;
		justify-content: space-between;
		align-items: flex-start;
		margin-bottom: 2.5rem;
		gap: 40px;

		@media (max-width: 768px) {
			flex-direction: column;
			align-items: flex-start;
			gap: 24px;
		}
	}

	.view-all {
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 2.5rem;

		@media (max-width: 768px) {
			width: 100%;
		}
	}

	.reads-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 16px;

		@media (max-width: 1024px) {
			grid-template-columns: repeat(2, 1fr);
		}

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
			gap: 50px;
		}
	}

	.read-card {
		overflow: hidden;
		background: #f5f5f5;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		cursor: pointer;
		position: relative;
		display: flex;
		flex-direction: column;
		height: 100%;
		border-radius: 1rem;
		padding: 16px;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);
			}
		}
	}

	.read-image {
		width: 100%;
		height: 240px;
		overflow: hidden;
		position: relative;
		flex-shrink: 0;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			display: block;
			border-radius: 1rem;
			transition: transform 0.4s ease;
		}
	}

	.read-content {
		position: relative;
		z-index: 2;
		flex-grow: 1;
		display: flex;
		flex-direction: column;
	}

	.read-date {
		font-size: 12px;
		margin: 0 0 12px 0;
		text-transform: uppercase;
		// letter-spacing: 0.8px;
		color: rgba(80, 80, 100, 0.7);
		font-weight: 500;
	}

	.read-content h3 {
		font-size: 18px;
		font-weight: 600;
		margin: 16px 0 12px;
		color: #1a1a1a;

		@media (max-width: 768px) {
			font-size: 18px;
		}
	}

	.read-description {
		font-size: 15px;
		margin: 0;
		color: #666;
		flex-grow: 1;
	}

	:global(html[data-theme='dark']) .read-card {
		background: #27272a;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);
			}
		}
	}

	:global(html[data-theme='dark']) .read-date {
		color: rgba(238, 231, 222, 0.6);
	}

	:global(html[data-theme='dark']) .read-content h3 {
		color: #fff;
	}

	:global(html[data-theme='dark']) .read-description {
		color: #aaa;
	}
</style>
