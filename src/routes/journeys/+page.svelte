<script>
	import { onMount } from 'svelte';

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

	let journeysVisible = $state(false);

	onMount(() => {
		// Small delay to ensure DOM is ready
		setTimeout(() => {
			journeysVisible = true;
		}, 100);
	});
</script>

<section class="journeys-hero">
	<div class="container">
		<h1 class="hero-title">Customer Journeys</h1>
		<p class="hero-subtitle">
			Real client stories showing how I help families find their perfect homes and reach their
			property goals.
		</p>
	</div>
</section>

<section class="journeys-container">
	<div class="container">
		<div class="journeys-grid">
			{#each journeys as journey, i}
				<article class="journey-card" class:visible={journeysVisible} style="--delay: {i}">
					<div class="journey-image">
						<img src={journey.photo} alt={journey.name} loading="lazy" />
					</div>
					<div class="journey-content">
						<h2>{journey.name}</h2>
						<div class="journey-text">
							{#each journey.review as paragraph}
								<p>{paragraph}</p>
							{/each}
						</div>
						<a href="/journeys/{journey.name}" class="read-full-story">Read Full Story</a>
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

	.journeys-hero {
		background: linear-gradient(135deg, #f5f5f5 0%, #e9ecef 100%);
		color: #000;
		padding: 80px 0 60px;
		text-align: center;

		.hero-title {
			font-size: 2.5rem;
			font-weight: 700;
			margin: 0 0 16px 0;
			line-height: 1.2;

			@media (max-width: 768px) {
				font-size: 36px;
			}
		}

		.hero-subtitle {
			font-size: 20px;
			color: #666;
			max-width: 600px;
			margin: 0 auto;
			opacity: 0.9;

			@media (max-width: 768px) {
				font-size: 16px;
				max-width: 400px;
			}
		}
	}

	:global(html[data-theme='dark']) .journeys-hero {
		background: linear-gradient(135deg, #1a1a1a 0%, #2a2a2a 100%);
		color: #fff;

		.hero-title {
			color: #fff;
		}

		.hero-subtitle {
			color: #b0b0c0;
			opacity: 0.9;
		}
	}

	.journeys-container {
		padding: 80px 0;
		background: #fff;

		@media (max-width: 768px) {
			padding: 60px 0 40px;
		}
	}

	:global(html[data-theme='dark']) .journeys-container {
		background: #1a1a1a;
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
		border-radius: 1.5rem;
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

	:global(html[data-theme='dark']) .journey-card {
		background: #27272a;

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
			border-radius: 0.75rem;
			transition: transform 0.4s ease;
		}
	}

	.journey-content {
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

		h2 {
			font-size: 18px;
			margin: 0 0 8px 0;
			color: #1a1a1a;

			@media (max-width: 768px) {
				font-size: 16px;
			}
		}

		.read-full-story {
			display: inline-block;
			align-self: flex-start;
			margin-top: 12px;
			padding: 8px 16px;
			background: transparent;
			color: #3a3546;
			border: 2px solid #3a3546;
			border-radius: 50px;
			font-weight: 600;
			font-size: 0.9rem;
			text-decoration: none;
			cursor: pointer;
			transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
			box-shadow: none;

			@media (hover: hover) and (pointer: fine) {
				&:hover {
					background: #3a3546;
					color: #f8f8f8;
					box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
				}
			}

			:global(html[data-theme='dark']) & {
				background: transparent;
				color: #f8f8f8;
				border: 2px solid #f8f8f8;
				box-shadow: none;

				&:hover {
					background: #f8f8f8;
					color: #1a1a1a;
					box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
				}
			}
		}
	}

	:global(html[data-theme='dark']) .journey-content {
		h2 {
			color: #fff;
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

	:global(html[data-theme='dark']) .journey-text {
		color: #aaa;
	}
</style>
