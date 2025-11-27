<script>
	import favicon from '$lib/assets/favicon.png';
	import logo from '$lib/assets/logo.png';
	import logoFooter from '$lib/assets/logo-footer.png';
	import '@fontsource/poppins';
	import Icon from '@iconify/svelte';
	import '../main.scss';
	let { children } = $props();

	let isDark = $state(false);
	let isRotating = $state(false);

	function toggleTheme() {
		isRotating = true;
		isDark = !isDark;
		const theme = isDark ? 'dark' : 'light';
		document.documentElement.setAttribute('data-theme', theme);
		localStorage.setItem('theme', theme);

		// Reset rotation after animation completes
		setTimeout(() => {
			isRotating = false;
		}, 600);
	}

	function initTheme() {
		if (typeof window !== 'undefined') {
			const savedTheme = localStorage.getItem('theme');
			isDark =
				savedTheme === 'dark' ||
				(savedTheme === null && window.matchMedia('(prefers-color-scheme: dark)').matches);

			const theme = isDark ? 'dark' : 'light';
			document.documentElement.setAttribute('data-theme', theme);
		}
	}

	// Initialize theme on mount
	$effect(() => {
		initTheme();
	});
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav class="navbar-container">
	<div class="navbar-brand">
		<a href="/" class="home-link">
			<img src={logo} alt="Logo" class="logo" />
		</a>
	</div>

	<ul class="navbar-menu">
		<li><a href="/" class="nav-link">Home</a></li>
		<li><a href="/about" class="nav-link">About</a></li>
		<li class="dropdown">
			<div class="nav-link">
				<span>Services</span>
				<Icon icon="mingcute:down-line" width="20" height="20" />
			</div>
			<ul class="dropdown-menu">
				<li>
					<a href="/services/planning-for-retirement"
						><Icon icon="mdi:piggy-bank" width="20" height="20" /><span
							>Planning for Retirement</span
						></a
					>
				</li>
				<li>
					<a href="/services/real-estate-consulting"
						><Icon icon="mdi:home-city" width="20" height="20" /><span>Real Estate Consulting</span
						></a
					>
				</li>
				<li>
					<a href="/services/asset-restructuring"
						><Icon icon="mdi:shuffle" width="20" height="20" /><span>Asset Restructuring</span></a
					>
				</li>
				<li>
					<a href="/services/selling-a-property"
						><Icon icon="mdi:tag-multiple" width="20" height="20" /><span>Selling a Property</span
						></a
					>
				</li>
				<li>
					<a href="/services/buying-a-property"
						><Icon icon="mdi:shopping" width="20" height="20" /><span>Buying a Property</span></a
					>
				</li>
				<li>
					<a href="/services/renting-a-property"
						><Icon icon="mdi:key" width="20" height="20" /><span>Renting a Property</span></a
					>
				</li>
			</ul>
		</li>
		<li><a href="/portfolio" class="nav-link">Portfolio</a></li>
		<li class="dropdown">
			<div class="nav-link">
				<span>Resources</span>
				<Icon icon="mingcute:down-line" width="20" height="20" />
			</div>
			<ul class="dropdown-menu">
				<li>
					<a href="/about"
						><Icon icon="mdi:information" width="20" height="20" /><span>About</span></a
					>
				</li>
				<li>
					<a href="/portfolio"
						><Icon icon="mdi:briefcase" width="20" height="20" /><span>Portfolio</span></a
					>
				</li>
				<li>
					<a href="/reads"
						><Icon icon="mdi:book-open" width="20" height="20" /><span>Featured Reads</span></a
					>
				</li>
				<li>
					<a href="/testimonials"
						><Icon icon="dashicons:testimonial" width="20" height="20" /><span>Testimonials</span
						></a
					>
				</li>
				<li>
					<a
						href="https://www.edgeprop.sg/analytic/edgefairvalue/condominium"
						target="_blank"
						rel="noopener noreferrer"
					>
						<Icon icon="mdi:chart-line" width="20" height="20" /><span>Property Valuation</span>
					</a>
				</li>
				<li>
					<a href="/financial-calculator"
						><Icon icon="mdi:calculator" width="20" height="20" /><span>Financial Calculator</span
						></a
					>
				</li>
			</ul>
		</li>
		<li><a href="/water-concept" class="nav-link">WATER Concept</a></li>
	</ul>

	<div class="navbar-actions">
		<button
			class="theme-toggle"
			onclick={toggleTheme}
			aria-label="Toggle theme"
			class:rotating={isRotating}
		>
			<Icon icon={isDark ? 'entypo:light-up' : 'solar:moon-line-duotone'} width="20" height="20" />
		</button>

		<a href="/contact" class="cta-button">Contact Me</a>
	</div>
</nav>

<a
	href="https://wa.me/6512345678"
	class="whatsapp-float"
	target="_blank"
	rel="noopener noreferrer"
	aria-label="Chat on WhatsApp"
>
	<Icon icon="mdi:whatsapp" width="28" height="28" />
</a>

{@render children()}

<footer class="footer">
	<div class="footer-container">
		<div class="footer-brand">
			<div class="brand-header">
				<img src={logoFooter} alt="Logo" class="logo" />
			</div>
			<p class="brand-description">
				Your trusted real estate partner. Specializing in portfolio upgrading and strategic property
				investment with a systematic, data-driven approach.
			</p>
			<div class="social-links">
				<a href="#" aria-label="Facebook">
					<Icon icon="mdi:facebook" width="24" height="24" />
				</a>
				<a href="#" aria-label="LinkedIn">
					<Icon icon="mdi:linkedin" width="24" height="24" />
				</a>
				<a href="#" aria-label="Instagram">
					<Icon icon="mdi:instagram" width="24" height="24" />
				</a>
				<a href="#" aria-label="WhatsApp">
					<Icon icon="mdi:whatsapp" width="24" height="24" />
				</a>
			</div>
		</div>

		<div class="footer-column">
			<h3>Services</h3>
			<ul>
				<li><a href="/services/planning-for-retirement">Planning for Retirement</a></li>
				<li><a href="/services/real-estate-consulting">Real Estate Consulting</a></li>
				<li><a href="/services/asset-restructuring">Asset Restructuring</a></li>
				<li><a href="/services/selling-a-property">Selling a Property</a></li>
				<li><a href="/services/buying-a-property">Buying a Property</a></li>
				<li><a href="/services/renting-a-property">Renting a Property</a></li>
			</ul>
		</div>

		<div class="footer-column">
			<h3>Resources</h3>
			<ul>
				<li><a href="/about">About</a></li>
				<li><a href="/portfolio">Portfolio</a></li>
				<li><a href="/reads">Featured Reads</a></li>
				<li><a href="/testimonials">Testimonials</a></li>
				<li>
					<a
						href="https://www.edgeprop.sg/analytic/edgefairvalue/condominium"
						target="_blank"
						rel="noopener noreferrer"
					>
						Property Valuation
					</a>
				</li>
				<li><a href="/financial-calculator">Financial Calculator</a></li>
			</ul>
		</div>

		<div class="footer-column">
			<h3>Contact</h3>
			<ul>
				<li><a href="/contact">Get In Touch</a></li>
				<li><a href="tel:+6512345678">+65 1234 5678</a></li>
				<li><a href="mailto:info@yourdomain.com">info@yourdomain.com</a></li>
				<li><a href="/contact">Schedule Consultation</a></li>
			</ul>
		</div>
	</div>

	<div class="footer-bottom">
		<p>Copyright © {new Date().getFullYear()} Brand. All rights reserved.</p>
		<div class="footer-links">
			<a href="/privacy-policy">Privacy Policy</a>
		</div>
	</div>
</footer>

<style lang="scss">
	:global(body) {
		margin: 0;
		padding: 0;
		font-family: 'Poppins', sans-serif;
	}

	/* Light Mode (Default) */
	:global(html[data-theme='light']) {
		color-scheme: light;
	}

	:global(html[data-theme='light']) :global(body) {
		background-color: #ffffff;
		color: #333333;
	}

	/* Dark Mode */
	:global(html[data-theme='dark']) {
		color-scheme: dark;
	}

	:global(html[data-theme='dark']) :global(body) {
		background-color: #1a1a1a;
		color: #eee7de;
	}

	.navbar-container {
		position: sticky;
		top: 0;
		z-index: 1000;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 16px 32px;
		background: #ffffff;
		border-bottom: 1px solid #eee7de;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
		transition: all 0.3s ease;

		&:hover {
			box-shadow:
				0 12px 48px rgba(0, 0, 0, 0.15),
				inset 0 1px 0 rgba(255, 255, 255, 0.15);
		}
	}

	:global(html[data-theme='dark']) .navbar-container {
		background: rgba(42, 42, 42, 0.7);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
		border: 1px solid rgba(255, 255, 255, 0.1);
		color: #eee7de;
		border-bottom-color: rgba(255, 255, 255, 0.1);
		box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);

		&:hover {
			box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
			background: rgba(42, 42, 42, 0.8);
		}
	}

	.navbar-brand {
		display: flex;
		align-items: center;
		gap: 12px;

		.logo {
			width: 150px;
			height: auto;
		}

		.brand-name {
			font-size: 20px;
			font-weight: 700;
		}
	}

	.navbar-menu {
		display: flex;
		list-style: none;
		margin: 0;
		padding: 0;
		gap: 8px;

		li {
			position: relative;
		}

		.dropdown {
			position: relative;

			.dropdown-menu {
				display: none;
				position: absolute;
				top: 100%;
				left: 0;
				background: #fff;
				box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
				border-radius: 6px;
				padding: 10px;
				min-width: 230px;
				list-style: none;
				z-index: 1000;

				li a {
					display: flex;
					align-items: center;
					gap: 10px;
					padding: 10px 16px;
					color: #333;
					text-decoration: none;
					font-size: 14px;
					border-radius: 6px;
					transition: all 0.3s ease;

					&:hover {
						background: #f7f7f7;
						color: black;
						transform: none;
					}
				}
			}

			&:hover .dropdown-menu {
				display: block;
			}
		}
	}

	.navbar-actions {
		display: flex;
		align-items: center;
		gap: 8px;
	}

	:global(html[data-theme='dark']) .dropdown-menu {
		background: rgba(51, 51, 51, 0.8) !important;
		backdrop-filter: blur(10px) !important;
		-webkit-backdrop-filter: blur(10px) !important;
		border: 1px solid rgba(255, 255, 255, 0.1) !important;
		color: #eee7de !important;
		box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3) !important;

		li a {
			color: #eee7de !important;

			&:hover {
				background: rgba(255, 255, 255, 0.1) !important;
				color: #fff !important;
			}
		}
	}

	.nav-link {
		display: inline-flex;
		align-items: center;
		padding: 5px 10px;
		gap: 4px;
		color: black;
		text-decoration: none;
		position: relative;
		transition: all 0.3s ease;

		&::after {
			content: '';
			position: absolute;
			bottom: 0;
			left: 0;
			width: 100%;
			height: 2px;
			background: black;
			transform: scaleX(0);
			transform-origin: left;
			transition: transform 0.3s ease;
		}

		&:hover::after {
			transform: scaleX(1);
		}

		&:hover :global(svg) {
			transform: rotate(180deg);
		}

		:global(svg) {
			transition: transform 0.3s ease;
		}
	}

	:global(html[data-theme='dark']) .nav-link {
		color: #eee7de;

		&::after {
			background: #eee7de;
		}
	}

	.theme-toggle {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 40px;
		height: 40px;
		background: transparent;
		border: none;
		color: #333;
		border-radius: 50%;
		cursor: pointer;
		transition: background 0.3s ease;
		margin: 0;

		&:hover {
			background: #f0f0f0;
		}

		&.rotating :global(svg) {
			animation: spin 0.6s ease-in-out;
		}
	}

	@keyframes spin {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}

	:global(html[data-theme='dark']) .theme-toggle {
		color: #eee7de;

		&:hover {
			background: rgba(255, 255, 255, 0.1);
		}
	}

	.cta-button {
		padding: 12px 28px;
		background: black;
		color: white;
		border: none;
		border-radius: 0.8rem;
		font-weight: 600;
		font-size: 15px;
		text-decoration: none;
		cursor: pointer;
		transition: all 0.3s ease;
		box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
		margin: 0;

		&:hover {
			transform: translateY(-2px);
			box-shadow: 0 6px 20px rgba(0, 0, 0, 0.4);
		}
	}

	:global(html[data-theme='dark']) .cta-button {
		background: rgba(255, 255, 255, 0.1);
		border: 1px solid rgba(255, 255, 255, 0.2);
		box-shadow: 0 8px 32px rgba(0, 0, 0, 0.2);

		&:hover {
			background: rgba(255, 255, 255, 0.15);
			border-color: rgba(255, 255, 255, 0.3);
		}
	}

	.whatsapp-float {
		position: fixed;
		bottom: 24px;
		right: 24px;
		width: 56px;
		height: 56px;
		background: rgba(37, 211, 102, 0.8);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
		border: 1px solid rgba(255, 255, 255, 0.2);
		color: white;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		box-shadow: 0 8px 32px rgba(37, 211, 102, 0.4);
		z-index: 999;
		transition: all 0.3s ease;

		&:hover {
			transform: scale(1.1);
			background: rgba(37, 211, 102, 0.9);
			box-shadow: 0 8px 32px rgba(37, 211, 102, 0.6);
		}

		@media (max-width: 768px) {
			width: 50px;
			height: 50px;
			bottom: 20px;
			right: 20px;
		}
	}

	.footer {
		// margin-top: 80px;
		background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
		color: #333;
		border-top: 1px solid #eee7de;
	}

	:global(html[data-theme='dark']) .footer {
		background: linear-gradient(135deg, rgba(31, 31, 31, 0.7) 0%, rgba(42, 42, 42, 0.7) 100%);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
		border-top: 1px solid rgba(255, 255, 255, 0.1);
	}

	.footer-container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 30px;
		display: grid;
		grid-template-columns: 2fr 1fr 1fr 1fr;
		gap: 48px;

		@media (max-width: 768px) {
			grid-template-columns: repeat(2, 1fr);
			gap: 1.5rem;
			padding: 40px 20px;

			.footer-brand {
				grid-column: 1 / -1;
			}
		}
	}

	.footer-brand {
		display: flex;
		flex-direction: column;
		gap: 16px;

		.brand-header {
			display: flex;
			align-items: center;
			gap: 12px;

			.logo {
				width: 150px;
				height: auto;
			}
		}

		.brand-description {
			color: #666;
			line-height: 1.6;
			font-size: 14px;
		}

		.social-links {
			display: flex;
			gap: 12px;

			a {
				display: flex;
				align-items: center;
				justify-content: center;
				width: 40px;
				height: 40px;
				background: linear-gradient(
					135deg,
					rgba(255, 255, 255, 0.9) 0%,
					rgba(240, 240, 245, 0.8) 100%
				);
				backdrop-filter: blur(10px);
				-webkit-backdrop-filter: blur(10px);
				border: 1.5px solid rgba(255, 255, 255, 0.6);
				border-radius: 50%;
				color: #1a1a2e;
				transition: all 0.3s ease;
				box-shadow:
					0 4px 15px rgba(0, 0, 0, 0.08),
					inset 1px 1px 2px rgba(255, 255, 255, 0.8);

				&:hover {
					transform: translateY(-4px);
					background: linear-gradient(
						135deg,
						rgba(255, 255, 255, 0.95) 0%,
						rgba(245, 245, 250, 0.85) 100%
					);
					box-shadow:
						0 8px 25px rgba(0, 0, 0, 0.12),
						inset 1px 1px 2px rgba(255, 255, 255, 0.9);
				}
			}
		}
	}

	:global(html[data-theme='dark']) .footer-brand .brand-description {
		color: #aaa;
	}

	:global(html[data-theme='dark']) .footer-brand .social-links a {
		background: linear-gradient(135deg, rgba(50, 50, 70, 0.4) 0%, rgba(40, 40, 60, 0.35) 100%);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
		border: 1.5px solid rgba(255, 255, 255, 0.12);
		color: #d0d0d0;
		box-shadow:
			0 4px 15px rgba(0, 0, 0, 0.3),
			inset 1px 1px 2px rgba(255, 255, 255, 0.08);

		&:hover {
			background: linear-gradient(135deg, rgba(70, 75, 100, 0.5) 0%, rgba(50, 55, 80, 0.45) 100%);
			border-color: rgba(255, 255, 255, 0.2);
			box-shadow:
				0 8px 25px rgba(0, 0, 0, 0.4),
				inset 1px 1px 2px rgba(255, 255, 255, 0.12);
		}
	}

	.footer-column {
		h3 {
			font-size: 16px;
			font-weight: 600;
			margin-bottom: 20px;
			color: black;
		}

		ul {
			list-style: none;
			padding: 0;
			margin: 0;
			display: flex;
			flex-direction: column;
			gap: 12px;

			li a {
				color: #666;
				text-decoration: none;
				font-size: 14px;
				transition: all 0.3s ease;
				display: inline-block;

				&:hover {
					color: black;
					transform: translateX(4px);
				}
			}
		}
	}

	:global(html[data-theme='dark']) .footer-column {
		h3 {
			color: #eee7de;
		}

		ul li a {
			color: #aaa;

			&:hover {
				color: #eee7de;
			}
		}
	}

	.footer-bottom {
		max-width: 1200px;
		margin: 0 auto;
		padding: 24px 32px;
		border-top: 1px solid #eee7de;
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 14px;
		color: #666;

		@media (max-width: 768px) {
			flex-direction: column;
			gap: 12px;
			padding: 20px 20px;
			text-align: center;
		}

		.footer-links {
			display: flex;
			gap: 24px;

			a {
				color: #666;
				text-decoration: none;
				transition: color 0.3s ease;

				&:hover {
					color: black;
				}
			}
		}
	}

	:global(html[data-theme='dark']) .footer-bottom {
		border-top: 1px solid rgba(255, 255, 255, 0.1);
		color: #aaa;

		.footer-links a {
			color: #aaa;

			&:hover {
				color: #eee7de;
			}
		}
	}

	@media (max-width: 768px) {
		.navbar-container {
			padding: 12px 16px;
			flex-wrap: wrap;
			gap: 12px;
		}

		.navbar-menu {
			display: none;
		}

		.navbar-brand {
			flex: 1;
		}
	}
</style>
