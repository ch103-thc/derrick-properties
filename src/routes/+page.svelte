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
			<div class="journey-photo-wrapper">
				<div class="journey-photo-large">
					<img src={journeys[currentJourney].photo} alt={journeys[currentJourney].name} />
				</div>
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
		<div class="reads-header">
			<div class="section-title" class:visible={readsVisible}>
				<h2>Featured Reads</h2>
				<p class="sub-header">Insights and updates from the real estate world</p>
			</div>
			<div class="see-all">
				<a href="/reads" class="see-all-btn">See All Reads</a>
			</div>
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
		padding: 16px 32px;
		background: #1a1a1a;
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

	.see-all-btn {
		display: inline-block;
		padding: 12px 20px;
		background: #1a1a1a;
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
	:global(html[data-theme='dark']) .see-all-btn {
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

		/* Layered frame effect - back layer */
		&::before {
			content: '';
			position: absolute;
			top: -20px;
			left: -20px;
			right: 20px;
			bottom: 20px;
			border: 2px solid #e0e0e0;
			border-radius: 1.5rem;
			z-index: 0;
		}
	}

	.info-image {
		position: relative;
		width: 100%;
		height: 500px;
		border-radius: 1.5rem;
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
		background: #e9ecef;

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	.section-title {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.6s ease;
		text-align: left;
		margin-bottom: 0;

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
			grid-template-columns: repeat(2, 1fr);
		}
	}

	.service-card {
		position: relative;
		border-radius: 1rem;
		overflow: hidden;
		height: 400px;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
		transition: all 0.3s ease;

		@media (max-width: 768px) {
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

	@media (hover: hover) and (pointer: fine) {
		.service-card:hover .service-image img {
			transform: scale(1.05);
		}

		.service-card:hover .service-info h3::after {
			transform: scaleX(1);
		}
	}

	.service-info {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		padding: 28px;
		background: linear-gradient(to top, rgba(0, 0, 0, 0.9), transparent);
		color: white;

		@media (max-width: 768px) {
			padding: 20px;
		}

		h3 {
			font-size: 18px;
			margin: 0 0 8px 0;
			position: relative;
			display: inline-block;

			@media (max-width: 768px) {
				font-size: 16px;
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
			font-size: 15px;
			margin: 0;
			opacity: 0.9;
			line-height: 1.5;

			@media (max-width: 768px) {
				font-size: 14px;
			}
		}
	}

	:global(html[data-theme='dark']) .services {
		background: rgba(31, 31, 31, 0.7);
	}

	:global(html[data-theme='dark']) .service-info {
		h3 {
			color: #fff;
		}

		p {
			color: #fff;
		}
	}

	/* Journeys Styles */
	.journeys {
		padding: 100px 0 80px;

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	.journeys-header {
		display: flex;
		justify-content: space-between;
		align-items: flex-start;
		margin-bottom: 48px;

		.header-text {
			h2 {
				font-size: 32px;
				margin: 0;

				@media (max-width: 768px) {
					font-size: 1.5rem;
				}
			}
		}

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

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				background: #999;
				transform: scale(1.2);
			}
		}

		&.active {
			background: #333;
			width: 24px;
			border-radius: 5px;
		}

		@media (max-width: 768px) {
			width: 8px;
			height: 8px;

			&.active {
				width: 20px;
			}
		}
	}

	.nav-arrows {
		display: flex;
		gap: 12px;
	}

	.arrow-btn {
		width: 44px;
		height: 44px;
		background: transparent;
		border: 2px solid #1a1a1a;
		border-radius: 999px;
		cursor: pointer;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
		color: #1a1a1a;
	}

	:global(html[data-theme='dark']) .arrow-btn {
		background: transparent;
		border: 2px solid #f8f8f8;
		color: #f8f8f8;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
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

	.journey-photo-wrapper {
		position: relative;
		width: 100%;
		position: sticky;
		top: 20px;

		@media (max-width: 968px) {
			position: relative;
			top: 0;
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
			border-radius: 1.5rem;
			z-index: 0;
		}
	}

	.journey-photo-large {
		position: relative;
		width: 100%;
		height: 500px;
		border-radius: 1.5rem;
		overflow: hidden;
		box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15);
		z-index: 2;

		@media (max-width: 968px) {
			height: 400px;
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
		font-size: 1rem;
		line-height: 1.7;
		margin: 0 0 20px 0;
		white-space: pre-line;
	}

	.reviewer {
		font-size: 1rem;
		font-weight: bold;
	}

	:global(html[data-theme='dark']) .journeys-header .header-text h2 {
		color: #fff;
	}

	:global(html[data-theme='dark']) .indicator-dot {
		background: #555;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				background: #777;
			}
		}

		&.active {
			background: #fff;
		}
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
		background: #e9ecef;

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	:global(html[data-theme='dark']) .reads {
		background: rgba(31, 31, 31, 0.7);
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

	.see-all {
		display: flex;
		align-items: flex-start;
		padding-top: 8px;

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
			gap: 20px;
		}
	}

	.read-card {
		border-radius: 1rem;
		overflow: hidden;
		background: #fff;
		border: 1px solid #e0e0e0;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		cursor: pointer;
		position: relative;
		display: flex;
		flex-direction: column;
		height: 100%;

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-4px);
				background: #fafafa;
				border-color: #d0d0d0;
				box-shadow: 0 4px 12px rgba(0, 0, 0, 0.12);
			}
		}
	}

	@media (hover: hover) and (pointer: fine) {
		.read-card:hover .read-image img {
			transform: scale(1.08);
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
			transition: transform 0.4s ease;
		}
	}

	.read-content {
		padding: 24px;
		background: rgba(255, 255, 255, 0.7);
		border-top: 1px solid rgba(0, 0, 0, 0.05);
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
		font-size: 20px;
		font-weight: 600;
		margin: 0 0 12px 0;
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
		background: #3a3a3a;
		border: 1px solid rgba(255, 255, 255, 0.12);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);

		@media (hover: hover) and (pointer: fine) {
			&:hover {
				transform: translateY(-4px);
				background: #4a4a4a;
				border-color: rgba(255, 255, 255, 0.2);
				box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
			}
		}
	}

	:global(html[data-theme='dark']) .read-content {
		background: rgba(30, 30, 40, 0.5);
		border-top-color: rgba(255, 255, 255, 0.05);
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
