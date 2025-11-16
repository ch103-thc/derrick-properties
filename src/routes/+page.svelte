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
				'Optimize your property portfolio through restructuring strategies that enhance long-term financial growth.'
		},
		{
			image: 'img/service/selling.png',
			title: 'Selling a Property',
			description:
				'Comprehensive guidance to position, market, and sell your property at the best possible price.'
		},
		{
			image: 'img/service/buying.png',
			title: 'Buying a Property',
			description:
				'Personalized support to help you find the right home or investment property that fits your goals.'
		},
		{
			image: 'img/service/renting.png',
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
		},
		{
			review: [
				'Some journeys in life come full circle. I’ve known Lau for almost 30 years — I even attended his wedding back then. So when he reached out recently, it was with a heavy heart… he needed help selling his 4-room flat due to a divorce.',
				'The unit was on a very low floor, though it had great conveniences: a 5-minute walk to the MRT, and close to parks, coffeeshops, and schools. Even with a relatively young lease, finding the right buyer wasn’t easy. And with the court order timeline ticking, the pressure was real.',
				'We went all out — digital marketing, paper flyers, door-knocking around the neighbourhood — hoping to connect with buyers who already loved the area and wanted to move here for the schools or MRT access. After six months of persistence and countless efforts, a genuine buyer finally appeared, and we secured the OTP.',
				'But the journey didn’t end there. Navigating his next home purchase was another challenge — limited funds, CPF retirement sum requirements, and strict loan eligibility. There were many rounds of calculations, appeals, and letters to the relevant agencies. Eventually, we managed to secure the minimum HDB loan he needed to move forward with a new flat.',
				'While not every story begins or ends the way we wish, being able to help Lau transition into a new chapter — together with his son and daughter — is something that truly gives meaning to my work. 💛'
			],
			name: "Lau's Story",
			photo: 'img/journey/lau-story.jpeg'
		}
	];

	const reads = [
		{
			image: 'https://images.unsplash.com/photo-1560518883-ce09059eeffa?w=800',
			date: 'Nov 5, 2025',
			title: 'Understanding Property Market Trends in 2025',
			description:
				'Key insights into the evolving real estate landscape and what it means for investors and homeowners.'
		},
		{
			image: 'https://images.unsplash.com/photo-1582407947304-fd86f028f716?w=800',
			date: 'Oct 28, 2025',
			title: 'Portfolio Upgrading: A Strategic Approach',
			description:
				'Learn how to systematically upgrade your property portfolio for long-term wealth growth.'
		},
		{
			image: 'https://images.unsplash.com/photo-1554224155-8d04cb21cd6c?w=800',
			date: 'Oct 15, 2025',
			title: 'Overseas Property Investment Guide',
			description:
				'Essential considerations when evaluating international real estate opportunities.'
		}
	];

	let currentJourney = $state(0);

	function nextJourney() {
		currentJourney = (currentJourney + 1) % journeys.length;
	}

	function prevJourney() {
		currentJourney = currentJourney === 0 ? journeys.length - 1 : currentJourney - 1;
	}

	import { onMount } from 'svelte';

	// Add after your existing state variables
	let servicesVisible = $state(false);
	let readsVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						if (entry.target.classList.contains('services')) {
							servicesVisible = true;
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
		const readsSection = document.querySelector('.reads');

		if (servicesSection) observer.observe(servicesSection);
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
					Specializing in portfolio upgrading, I help clients make informed decisions that align
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
						<img src={service.image} alt={service.title} />
					</div>
					<div class="service-info">
						<h3>{service.title}</h3>
						<p>{service.description}</p>
					</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- Journeys Section -->
<section class="journeys">
	<div class="container">
		<div class="journeys-header">
			<div class="header-text">
				<h2>My Customer's Journey With Me</h2>
			</div>

			<div class="nav-arrows">
				<button class="arrow-btn" onclick={prevJourney}>
					<Icon icon="mingcute:left-line" width="24" height="24" />
				</button>
				<button class="arrow-btn" onclick={nextJourney}>
					<Icon icon="mingcute:right-line" width="24" height="24" />
				</button>
			</div>

			<div class="journey-indicators">
				{#each journeys as _, index}
					<button
						class="indicator-dot"
						class:active={currentJourney === index}
						onclick={() => (currentJourney = index)}
						aria-label="Go to journey {index + 1}"
					></button>
				{/each}
			</div>
		</div>

		<div class="journey-content">
			<div class="journey-photo-large">
				<img src={journeys[currentJourney].photo} alt={journeys[currentJourney].name} />
			</div>
			<div class="journey-text-scroll">
				<div class="review-wrapper">
					{#each journeys[currentJourney].review as paragraph}
						<p class="review">{paragraph}</p>
					{/each}
				</div>
				<p class="reviewer">— {journeys[currentJourney].name}</p>
			</div>
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
						<p class="read-date">{read.date}</p>
						<h3>{read.title}</h3>
						<p class="read-description">{read.description}</p>
					</div>
				</article>
			{/each}
		</div>

		<div class="see-all">
			<a href="/reads" class="see-all-btn">See All Reads</a>
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
		background: white;
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
			font-size: 1.8rem;
			margin: 0 0 24px 0;
			line-height: 1.2;
		}

		p {
			font-size: 1rem;
			line-height: 1.7;
			color: #666;
			margin: 0 0 20px 0;
			max-width: 590px;

			&:last-child {
				margin-bottom: 0;
			}
		}
	}

	.info-image-wrapper {
		position: relative;
		width: 100%;

		@media (max-width: 768px) {
			order: -1;
		}

		/* Layered frame effect - back layer */
		&::before {
			content: '';
			position: absolute;
			top: -20px;
			left: -20px;
			right: 20px;
			bottom: 20px;
			border: 2px solid #e0e0e0;
			border-radius: 0.25rem;
			z-index: 0;
		}

		/* Optional: Second layer for triple effect */
		// &::after {
		// 	content: '';
		// 	position: absolute;
		// 	top: -10px;
		// 	left: -10px;
		// 	right: 10px;
		// 	bottom: 10px;
		// 	border: 2px solid #f0f0f0;
		// 	border-radius: 0.25rem;
		// 	z-index: 1;
		// }
	}

	.info-image {
		position: relative;
		width: 100%;
		height: 500px;
		border-radius: 0.25rem;
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
	}

	.section-title {
		text-align: center;
		margin-bottom: 56px;

		h2 {
			font-size: 1.8rem;
			margin: 0 0 12px 0;
		}

		.sub-header {
			font-size: 18px;
			color: #666;
			margin: 0;
		}
	}

	.services-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 32px;

		@media (max-width: 1024px) {
			grid-template-columns: repeat(2, 1fr);
		}

		@media (max-width: 640px) {
			grid-template-columns: repeat(2, 1fr);
			gap: 16px;
		}
	}

	.service-card {
		position: relative;
		border-radius: 0.25rem;
		overflow: hidden;
		height: 400px;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
		transition: all 0.3s ease;

		@media (max-width: 640px) {
			height: 300px;
		}
	}

	.service-image {
		width: 100%;
		height: 100%;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			transition: transform 0.3s ease;
		}
	}

	.service-card:hover .service-image img {
		transform: scale(1.05);
	}

	.service-info {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		padding: 28px;
		background: linear-gradient(to top, rgba(0, 0, 0, 0.9), transparent);
		color: white;

		h3 {
			font-size: 1.5rem;
			margin: 0 0 8px 0;
			position: relative;
			display: inline-block;

			@media (max-width: 640px) {
				font-size: 1rem;
			}

			&::after {
				content: '';
				position: absolute;
				bottom: -2px;
				left: 0;
				width: 100%;
				height: 2px;
				background: white;
				transform: scaleX(0);
				transform-origin: left;
				transition: transform 0.3s ease;
			}
		}

		p {
			font-size: 1rem;
			margin: 0;
			opacity: 0.9;
			line-height: 1.5;

			@media (max-width: 640px) {
				font-size: 0.8rem;
			}
		}
	}

	.service-card:hover .service-info h3::after {
		transform: scaleX(1);
	}

	/* Journeys Styles */
	.journeys {
		padding: 100px 0 80px;
		background: #f8f8f8;
	}

	.journeys-header {
		display: flex;
		justify-content: space-between;
		align-items: flex-start;
		margin-bottom: 48px;

		@media (max-width: 768px) {
			flex-direction: column;
			gap: 24px;
		}
	}

	.journey-indicators {
		display: flex;
		gap: 8px;
		align-items: center;
	}

	.indicator-dot {
		width: 10px;
		height: 10px;
		border-radius: 50%;
		background: #d0d0d0;
		border: none;
		cursor: pointer;
		transition: all 0.3s ease;
		padding: 0;

		&:hover {
			background: #999;
			transform: scale(1.2);
		}

		&.active {
			background: #333;
			width: 24px;
			border-radius: 5px;
		}
	}

	.nav-arrows {
		display: flex;
		gap: 12px;
	}

	.arrow-btn {
		width: 48px;
		height: 48px;
		background: white;
		border: 2px solid #e0e0e0;
		border-radius: 999px;
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: all 0.3s ease;

		&:hover {
			border-color: #333;
			background: rgba(0, 0, 0, 0.05);
		}
	}

	.journey-content {
		display: grid;
		grid-template-columns: 50% 1fr;
		gap: 56px;
		align-items: start;

		@media (max-width: 968px) {
			grid-template-columns: 1fr;
			gap: 32px;
		}
	}

	.journey-photo-large {
		width: 100%;
		height: 500px;
		border-radius: 8px;
		overflow: hidden;
		box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15);
		position: sticky;
		top: 20px;

		@media (max-width: 968px) {
			height: 400px;
			position: relative;
			top: 0;
		}

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
		}
	}

	.journey-text-scroll {
		padding: 20px 0;

		@media (max-width: 968px) {
			padding: 0;
		}
	}

	.review-wrapper {
		max-height: 450px;
		overflow-y: auto;
		padding-right: 16px;
		margin-bottom: 28px;

		&::-webkit-scrollbar {
			width: 8px;
		}

		&::-webkit-scrollbar-track {
			background: #f1f1f1;
			border-radius: 10px;
		}

		&::-webkit-scrollbar-thumb {
			background: #ccc;
			border-radius: 10px;

			&:hover {
				background: #999;
			}
		}
	}

	.review {
		line-height: 1.8;
		color: #333;
		margin: 0 0 20px 0;
		white-space: pre-line;

		@media (max-width: 768px) {
			font-size: 17px;
		}
	}

	.reviewer {
		font-weight: bold;
	}

	/* Reads Styles */
	.reads {
		padding: 100px 0 80px;
		background: white;
	}

	.reads-grid {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		gap: 32px;

		@media (max-width: 1024px) {
			grid-template-columns: repeat(2, 1fr);
		}

		@media (max-width: 640px) {
			grid-template-columns: 1fr;
		}
	}

	.read-card {
		background: white;
		border-radius: 0.25rem;
		overflow: hidden;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
		transition: all 0.3s ease;
		cursor: pointer;

		&:hover {
			transform: translateY(-4px);
			box-shadow: 0 8px 30px rgba(0, 0, 0, 0.12);
		}
	}

	.read-image {
		width: 100%;
		height: 240px;
		overflow: hidden;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			transition: transform 0.3s ease;
		}
	}

	.read-card:hover .read-image img {
		transform: scale(1.05);
	}

	.read-content {
		padding: 24px;
	}

	.read-date {
		font-size: 14px;
		color: #999;
		margin: 0 0 12px 0;
		text-transform: uppercase;
		letter-spacing: 0.5px;
	}

	.read-content h3 {
		font-size: 20px;
		font-weight: 600;
		margin: 0 0 12px 0;
		line-height: 1.4;
		color: #333;
	}

	.read-description {
		font-size: 15px;
		line-height: 1.6;
		color: #666;
		margin: 0;
	}

	.see-all {
		text-align: center;
		margin-top: 40px;

		.see-all-btn {
			display: inline-block;
			padding: 12px 28px;
			background: black;
			color: white;
			border: none;
			border-radius: 0.25rem;
			font-weight: 600;
			font-size: 15px;
			text-decoration: none;
			cursor: pointer;
			transition: all 0.3s ease;
			box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);

			&:hover {
				transform: translateY(-2px);
				box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4);
			}
		}
	}

	.section-title {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.6s ease;

		&.visible {
			opacity: 1;
			transform: translateY(0);
		}

		h2 {
			transition-delay: 0.1s;
		}

		.sub-header {
			transition-delay: 0.2s;
		}
	}

	.service-card,
	.read-card {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.6s ease;
		transition-delay: calc(0.4s + var(--delay) * 0.15s);

		&.visible {
			opacity: 1;
			transform: translateY(0);
		}
	}
</style>
