<script>
	import Icon from '@iconify/svelte';

	const services = [
		{
			image: 'img/service/retirement.jpg',
			title: 'Planning for Retirement',
			url: 'planning-for-retirement',
			description:
				'Strategic real estate planning for long-term security and stable retirement income.'
		},
		{
			image: 'img/service/consulting.jpg',
			title: 'Real Estate Consulting',
			url: 'real-estate-consulting',
			description:
				'Expert guidance for buying, selling, investing, and renting real estate for passive income.'
		},
		{
			image: 'img/service/restructuring.jpg',
			title: 'Asset Restructuring',
			url: 'asset-restructuring',
			description:
				'Optimise your property portfolio with restructuring strategies for long-term growth.'
		},
		{
			image: 'img/service/selling.jpeg',
			title: 'Selling a Property',
			url: 'selling-a-property',
			description:
				'Strategic guidance to position, market, and sell your property for the best price.'
		},
		{
			image: 'img/service/buying.jpeg',
			title: 'Buying a Property',
			url: 'buying-a-property',
			description: 'Personalised support to find the right home or investment property.'
		},
		{
			image: 'img/service/renting.jpeg',
			title: 'Renting a Property',
			url: 'renting-a-property',
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
		},
		{
			review: [
				'Rafi first reached out to me after seeing my FB story about how I helped Emilia, a single buyer, secure her 3-room flat. At that time, his situation was tough — he was working as a food delivery rider, his wife was on an LTVP and not working yet, and they were living in a rented flat under his mom’s name with their four growing children.',
				'He asked me a simple but heartfelt question: “Bro do you think I have any chance to give my family a home of our own?”',
				'But things weren’t straightforward. Rafi was under a bank loan restructuring program with two more years left, which made getting any housing loan extremely difficult. This was a genuine case that needed real guidance — not just a quick “no” like what he had heard from other agents.',
				'I sat down with him and mapped out a clear, realistic path forward: • secure a permanent job so he can qualify for an HDB loan • prioritise clearing his remaining debts • renew his wife’s passport and LTVP • eventually get her employed too, to strengthen the family’s income • understand how CPF can support the journey',
				'By the end of our conversation, he thanked me — saying most agents had turned him away once they heard his situation. I assured him that I was here to walk this journey with him, no matter how long it took.',
				'Fast forward two years. Rafi called me again — this time with good news. He had a stable, permanent job… and his wife had become a PR. That was the green light we needed. We met up, re-assessed everything, and moved forward with confidence.',
				'Today, Rafi and his family are proud owners of a 4-room flat, conveniently located near their daughter’s school and close to his sister’s house — making it easier for his mom to visit too.',
				'Seeing the smile on his face, and knowing how much this home means for his children’s future, reminds me why I do what I do. This profession isn’t just about homes — it’s about changing lives, one family at a time. 💛🏡✨',
				'If you’re unsure about your situation or feel like your chances are low - it’s okay. Sometimes you just need someone to show you the path. PM me anytime. I’m here to help.'
			],
			name: "Rafi's Story",
			photo: 'img/journey/rafi-story.jpeg'
		},
		{
			review: [
				'During one of our activities, Mrs Tay approached me with an interest in investing in a property. It was a broad desire — and like many first-time investors, she wasn’t sure what direction made the most sense for her goals.',
				'We had an open and honest chat about her current home, her finances, and what she hoped to achieve. Local commercial or industrial properties didn’t match her lifestyle or comfort level. Buying another local residential property under her daughter’s name also didn’t feel right, especially with her daughter just entering her graduation year.',
				'That narrowed our path to a meaningful, realistic option: ✨ a neighbouring overseas property — one that fit her budget, offered potential rental income, and aligned with her long-term plans.',
				'I connected her with my trusted cross-border partner to ensure we fully understood the policies and regulations involved. Protecting her interests was priority. Together, we reviewed options, analysed the rules, and even travelled across the border for site visits.',
				'And that’s when everything clicked. We found a development with beautiful natural surroundings — a unit with serene sea views right from the balcony, and from the higher floors, a sweeping view of the local township below. It offered both tranquility and vibrancy — exactly the kind of environment she could see value in for the long term.',
				'After several discussions and on-site evaluations, she made her decision with full confidence. Today, Mrs Tay is delighted — not just because she secured a promising investment, but because it aligns perfectly with her plans for her daughter’s future and her own retirement lifestyle.',
				'Property decisions aren’t just about numbers. They’re about clarity, care, and helping clients find a future they feel good about. 🌊🏡✨'
			],
			name: "Mrs Tay's Story",
			photo: 'img/journey/tay-story.jpeg'
		},
		{
			review: [
				'Viewing showflats is a favourite pastime for many people — and that’s exactly how I bumped into Mr Teh, a gentleman in his 50s, while I was on duty. We toured the showflat together, and soon after, we dived into a conversation about policies, numbers, and the realities of today’s property market.',
				'We analysed nearby projects, looked at both sale and rental trends, and discussed where the market is likely heading in the near future. These insights were important, especially for someone like Mr Teh — a finance professional who understands numbers better than anyone.',
				'Initially, the idea of owning a private investment-cum-own-stay property seemed too heavy on his finances. After reviewing the calculations together, it became clear that pushing for a private condo immediately wouldn’t be the most balanced move.',
				'That’s when we zoomed in on a more strategic path: ✨ Upgrading to an Executive Condo (EC) It made perfect sense — he could secure a new home without having to offload his existing property right away. More flexibility, less pressure, and better long-term planning.',
				'We went through several EC projects that fit his budget, lifestyle, and future plans. Keeping his son’s working location in mind, he eventually made a decisive choice: ✔ a project with a sizable land parcel ✔ facilities he could enjoy now ✔ and strong appeal for resale or retirement planning later',
				'Today, Mr Teh feels confident and excited about the road ahead — knowing he made a strategic, future-proof decision that balances his finances, lifestyle, and long-term goals.',
				'Helping clients see both numbers and possibilities… that’s where the magic happens. ✨🏡',
				'PM me if you are in search and needs a 2nd proposal to understand better. Always ready to assist.'
			],
			name: "Mr Teh's Story",
			photo: 'img/journey/teh-story.jpeg'
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

	let currentJourneyIndex = $state(0);
	const journeysPerPage = 3;
	const totalJourneyPages = Math.ceil(journeys.length / journeysPerPage);

	function nextJourneys() {
		if (currentJourneyIndex < totalJourneyPages - 1) {
			currentJourneyIndex++;
		}
	}

	function prevJourneys() {
		if (currentJourneyIndex > 0) {
			currentJourneyIndex--;
		}
	}

	function goToJourneyPage(index) {
		currentJourneyIndex = index;
	}

	$effect(() => {
		const startIdx = currentJourneyIndex * journeysPerPage;
		visibleJourneys = journeys.slice(startIdx, startIdx + journeysPerPage);
	});

	let visibleJourneys = $state(journeys.slice(0, journeysPerPage));

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
				<a
					href="/services/{service.url}"
					class="service-card"
					class:visible={servicesVisible}
					style="--delay: {i}"
				>
					<div class="service-image">
						<img src={service.image} alt={service.title} loading="lazy" />
						<div class="service-overlay">
							<h3>{service.title}</h3>
							<p>{service.description}</p>
							<span class="read-more">
								Read More
								<Icon icon="mingcute:right-line" width="20" height="20" />
							</span>
						</div>
					</div>
				</a>
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

		<div class="carousel-wrapper">
			<button
				class="nav-arrow prev"
				onclick={prevJourneys}
				disabled={currentJourneyIndex === 0}
				aria-label="Previous journeys"
			>
				<Icon icon="mdi:chevron-left" width="32" height="32" />
			</button>

			<div class="journeys-grid">
				{#each visibleJourneys as journey, i}
					<a
						href="/journeys/{journey.name}"
						class="journey-card"
						class:visible={journeysVisible}
						style="--delay: {i}"
					>
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
							<span class="read-full-story">
								Read Full Story
								<Icon icon="mingcute:right-line" width="20" height="20" />
							</span>
						</div>
					</a>
				{/each}
			</div>

			<button
				class="nav-arrow next"
				onclick={nextJourneys}
				disabled={currentJourneyIndex === totalJourneyPages - 1}
				aria-label="Next journeys"
			>
				<Icon icon="mdi:chevron-right" width="32" height="32" />
			</button>
		</div>

		<div class="carousel-indicators">
			{#each Array(totalJourneyPages) as _, i}
				<button
					class="indicator"
					class:active={currentJourneyIndex === i}
					onclick={() => goToJourneyPage(i)}
					aria-label="Go to page {i + 1}"
				/>
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
		</div>

		<div class="reads-grid">
			{#each reads as read, i}
				<a
					href="/reads/{read.title}"
					class="read-card"
					class:visible={readsVisible}
					style="--delay: {i}"
				>
					<div class="read-image">
						<img src={read.image} alt={read.title} loading="lazy" />
					</div>
					<div class="read-info">
						<p class="read-date">{read.date}</p>
						<h3>{read.title}</h3>
						<p class="read-description">{read.description}</p>
						<span class="read-article">
							Read Article
							<Icon icon="mingcute:right-line" width="20" height="20" />
						</span>
					</div>
				</a>
			{/each}
		</div>
		<div class="view-all">
			<a href="/reads" class="view-all-btn">View All Articles</a>
		</div>
	</div>
</section>

<style lang="scss">
	.container {
		max-width: 1135px;
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
		color: #fff;
		border-radius: 9999px;
		font-weight: 600;
		font-size: 1rem;
		text-align: center;
		text-decoration: none;
		cursor: pointer;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
		// letter-spacing: 0.5px;
		margin-top: 16px;

		@media (max-width: 768px) {
			width: 100%;
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
				background: #333;
			}
		}
	}

	:global(html[data-theme='dark']) .cta-button {
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

	:global(html[data-theme='dark']) .view-all-btn {
		background: transparent;
		color: #f8f8f8;
		border: 2px solid #f8f8f8;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				background: #f8f8f8;
				color: #1a1a1a;
				box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
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
		border-radius: 8px;
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

	/* Carousel Wrapper */
	.carousel-wrapper {
		position: relative;
		padding: 0 60px;

		@media (max-width: 768px) {
			padding: 0;
		}
	}

	/* Navigation Arrows */
	.nav-arrow {
		position: absolute;
		top: 50%;
		transform: translateY(-50%);
		background: rgba(58, 53, 70, 0.9);
		color: #fff;
		border: none;
		width: 48px;
		height: 48px;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		cursor: pointer;
		transition: all 0.3s ease;
		z-index: 10;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);

		&:disabled {
			opacity: 0.3;
			cursor: not-allowed;
		}

		&:not(:disabled) {
			@media (hover: hover) and (pointer: fine) {
				&:hover {
					background: rgba(58, 53, 70, 1);
					box-shadow: 0 4px 12px rgba(0, 0, 0, 0.25);
				}
			}
		}

		&.prev {
			left: 0;
		}

		&.next {
			right: 0;
		}

		@media (max-width: 768px) {
			display: none;
		}
	}

	:global(html[data-theme='dark']) .nav-arrow {
		background: rgba(248, 248, 248, 0.9);
		color: #1a1a1a;

		&:not(:disabled) {
			@media (hover: hover) and (pointer: fine) {
				&:hover {
					background: rgba(248, 248, 248, 1);
				}
			}
		}
	}

	/* Carousel Indicators */
	.carousel-indicators {
		display: flex;
		justify-content: center;
		gap: 8px;
		margin-top: 32px;

		@media (max-width: 768px) {
			display: none;
		}
	}

	.indicator {
		width: 8px;
		height: 8px;
		border-radius: 50%;
		border: none;
		background: #d1d5db;
		cursor: pointer;
		transition: all 0.3s ease;
		padding: 0;

		&.active {
			background: #3a3546;
			width: 24px;
			border-radius: 4px;
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover:not(.active) {
				background: #9ca3af;
			}
		}
	}

	:global(html[data-theme='dark']) .indicator {
		background: #52525b;

		&.active {
			background: #f8f8f8;
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover:not(.active) {
				background: #71717a;
			}
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
		border-radius: 12px;
		overflow: hidden;
		height: 320px;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		cursor: pointer;
		opacity: 0;
		transform: translateY(30px);
		text-decoration: none;
		color: inherit;

		&.visible {
			opacity: 1;
			transform: translateY(0);
			transition-delay: calc(var(--delay) * 0.1s);
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);

				.service-image img {
					transform: scale(1.05);
				}

				.read-more {
					gap: 12px;
				}
			}
		}
	}

	.service-image {
		position: relative;
		width: 100%;
		height: 100%;
		overflow: hidden;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			transition: transform 0.4s ease;
		}
	}

	.service-overlay {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		background: linear-gradient(
			to top,
			rgba(0, 0, 0, 0.65) 0%,
			rgba(0, 0, 0, 0.3) 25%,
			transparent 50%
		);
		padding: 24px;
		color: #fff;
		display: flex;
		flex-direction: column;
		justify-content: flex-end;
		height: 100%;

		h3 {
			font-size: 20px;
			margin: 0 0 12px 0;
			color: #fff;

			@media (max-width: 768px) {
				font-size: 18px;
			}
		}

		p {
			font-size: 15px;
			margin: 0 0 16px 0;
			line-height: 1.5;
			color: rgba(255, 255, 255, 0.9);

			@media (max-width: 768px) {
				font-size: 14px;
			}
		}

		.read-more {
			display: inline-flex;
			align-items: center;
			gap: 8px;
			color: rgba(255, 255, 255, 0.9);
			font-weight: 600;
			font-size: 0.9rem;
			text-decoration: none;
			cursor: pointer;
			transition: all 0.3s ease;
		}
	}

	:global(html[data-theme='dark']) .service-card {
		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);
			}
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
			display: flex;
			overflow-x: auto;
			scroll-snap-type: none;
			gap: 16px;
			padding-bottom: 16px;
			-webkit-overflow-scrolling: touch;

			&::-webkit-scrollbar {
				display: none;
			}

			-ms-overflow-style: none;
			scrollbar-width: none;
		}
	}

	.journey-card {
		position: relative;
		border-radius: 12px;
		overflow: visible;
		height: auto;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		cursor: pointer;
		display: flex;
		flex-direction: column;
		opacity: 0;
		transform: translateY(30px);
		text-decoration: none;
		color: inherit;

		&.visible {
			opacity: 1;
			transform: translateY(0);
			transition-delay: calc(var(--delay) * 0.1s);
		}

		@media (max-width: 768px) {
			flex: 0 0 85%;
			scroll-snap-align: none;
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);

				.read-full-story {
					gap: 12px;
				}
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
			border-radius: 12px;
			transition: transform 0.4s ease;
		}
	}

	.journey-info {
		position: relative;
		margin: 16px 0 16px;
		background: transparent;
		color: inherit;
		flex-grow: 1;
		display: flex;
		flex-direction: column;

		h3 {
			font-size: 18px;
			margin: 0 0 8px 0;
			color: #1a1a1a;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.read-full-story {
			display: inline-flex;
			align-items: center;
			gap: 8px;
			margin-top: 12px;
			color: #3a3546;
			font-weight: 600;
			font-size: 0.9rem;
			text-decoration: none;
			cursor: pointer;
			transition: all 0.3s ease;

			:global(html[data-theme='dark']) & {
				color: #f8f8f8;
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

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	.reads-grid {
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

	.view-all {
		text-align: center;
		margin-top: 40px;

		@media (max-width: 768px) {
			margin-top: 32px;
		}
	}

	.view-all-btn {
		display: inline-block;
		padding: 14px 28px;
		background: transparent;
		color: #3a3546;
		border: 2px solid #3a3546;
		border-radius: 9999px;
		font-weight: 600;
		font-size: 1rem;
		text-decoration: none;
		cursor: pointer;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);

		@media (max-width: 768px) {
			width: 100%;
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				background: #3a3546;
				color: #f8f8f8;
				box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
			}
		}
	}

	.read-card {
		position: relative;
		border-radius: 12px;
		overflow: visible;
		height: auto;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		cursor: pointer;
		display: flex;
		flex-direction: column;
		background: #f5f5f5;
		padding: 16px;
		opacity: 0;
		transform: translateY(30px);
		text-decoration: none;
		color: inherit;

		&.visible {
			opacity: 1;
			transform: translateY(0);
			transition-delay: calc(var(--delay) * 0.1s);
		}

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);

				.read-article {
					gap: 12px;
				}
			}
		}
	}

	.read-image {
		width: 100%;
		height: 240px;
		overflow: hidden;
		flex-shrink: 0;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			border-radius: 6px;
			transition: transform 0.4s ease;
		}
	}

	.read-info {
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

		.read-date {
			font-size: 13px;
			color: #999;
			margin: 0 0 8px 0;
			font-weight: 500;

			@media (max-width: 768px) {
				font-size: 12px;
			}
		}

		h3 {
			font-size: 18px;
			margin: 0 0 8px 0;
			color: #1a1a1a;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.read-description {
			font-size: 15px;
			margin: 0;
			line-height: 1.5;
			color: #666;
			flex-grow: 1;

			@media (max-width: 768px) {
				font-size: 14px;
			}
		}

		.read-article {
			display: inline-flex;
			align-items: center;
			gap: 8px;
			margin-top: 12px;
			color: #3a3546;
			font-weight: 600;
			font-size: 0.9rem;
			text-decoration: none;
			cursor: pointer;
			transition: all 0.3s ease;

			:global(html[data-theme='dark']) & {
				color: #f8f8f8;
			}
		}
	}

	:global(html[data-theme='dark']) .read-card {
		background: #27272a;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-2px);
			}
		}
	}

	:global(html[data-theme='dark']) .read-info {
		.read-date {
			color: #777;
		}

		h3 {
			color: #fff;
		}

		.read-description {
			color: #aaa;
		}
	}
</style>
