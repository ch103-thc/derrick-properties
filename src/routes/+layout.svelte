<script>
	import favicon from '$lib/assets/favicon.svg';
	import '@fontsource/poppins';
	import Icon from '@iconify/svelte';
	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav class="navbar-container">
	<div class="navbar-brand">
		<img src={favicon} alt="Logo" class="logo" />
		<span class="brand-name">Brand</span>
	</div>

	<ul class="navbar-menu">
		<li><a href="/" class="nav-link">Home</a></li>
		<li><a href="/about" class="nav-link">About</a></li>
		<li class="dropdown">
			<a href="/services" class="nav-link">
				<span>Services</span>
				<Icon icon="mingcute:down-line" width="18" height="18" />
			</a>
			<ul class="dropdown-menu">
				<li><a href="/services/property-management">Property Management</a></li>
				<li><a href="/services/consulting">Real Estate Consulting</a></li>
				<li><a href="/services/valuation">Property Valuation</a></li>
				<li><a href="/services/portfolio-upgrade">Portfolio Upgrading</a></li>
			</ul>
		</li>
		<li><a href="/portfolio" class="nav-link">Portfolio</a></li>
		<li class="dropdown">
			<a href="/resources" class="nav-link">
				<span>Resources</span>
				<Icon icon="mingcute:down-line" width="18" height="18" />
			</a>
			<ul class="dropdown-menu">
				<li><a href="/about">About</a></li>
				<li><a href="/portfolio">Portfolio</a></li>
				<li><a href="/reads">Featured Reads</a></li>
				<li><a href="/testimonials">Testimonials</a></li>
			</ul>
		</li>
		<li><a href="/water-concept" class="nav-link">Water Concept</a></li>
	</ul>

	<a href="/contact" class="cta-button">Contact Me</a>
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
				<img src={favicon} alt="Logo" class="logo" />
				<span class="brand-name">Brand</span>
			</div>
			<p class="brand-description">
				Your trusted real estate partner. Specializing in portfolio upgrading and strategic property
				investment with a systematic, data-driven approach.
			</p>
			<div class="social-links">
				<a href="#" aria-label="Facebook">
					<Icon icon="mdi:facebook" width="20" height="20" />
				</a>
				<a href="#" aria-label="LinkedIn">
					<Icon icon="mdi:linkedin" width="20" height="20" />
				</a>
				<a href="#" aria-label="Instagram">
					<Icon icon="mdi:instagram" width="20" height="20" />
				</a>
				<a href="#" aria-label="WhatsApp">
					<Icon icon="mdi:whatsapp" width="20" height="20" />
				</a>
			</div>
		</div>

		<div class="footer-column">
			<h3>Services</h3>
			<ul>
				<li><a href="/services/property-management">Property Management</a></li>
				<li><a href="/services/consulting">Real Estate Consulting</a></li>
				<li><a href="/services/valuation">Property Valuation</a></li>
				<li><a href="/services/portfolio-upgrade">Portfolio Upgrading</a></li>
			</ul>
		</div>

		<div class="footer-column">
			<h3>Resources</h3>
			<ul>
				<li><a href="/about">About</a></li>
				<li><a href="/portfolio">Portfolio</a></li>
				<li><a href="/reads">Featured Reads</a></li>
				<li><a href="/testimonials">Testimonials</a></li>
			</ul>
		</div>

		<div class="footer-column">
			<h3>Contact</h3>
			<ul>
				<li><a href="/contact">Get In Touch</a></li>
				<li><a href="tel:+6512345678">+65 1234 5678</a></li>
				<li><a href="mailto:info@yourdomain.com">info@yourdomain.com</a></li>
				<li><a href="/schedule">Schedule Consultation</a></li>
			</ul>
		</div>
	</div>

	<div class="footer-bottom">
		<p>© {new Date().getFullYear()} Brand. All rights reserved.</p>
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

	.navbar-container {
		position: sticky;
		top: 0;
		z-index: 1000;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 16px 32px;
		background: #ffffff;
		border-bottom: 1px solid #e5e5e5;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.05);
		transition: all 0.3s ease;

		&:hover {
			box-shadow:
				0 12px 48px rgba(0, 0, 0, 0.15),
				inset 0 1px 0 rgba(255, 255, 255, 0.15);
		}
	}

	.navbar-brand {
		display: flex;
		align-items: center;
		gap: 12px;

		.logo {
			width: 32px;
			height: 32px;
			transition: transform 0.3s ease;

			&:hover {
				transform: rotate(360deg);
			}
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
				min-width: 200px;
				list-style: none;
				z-index: 1000;

				li a {
					display: block;
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

	.cta-button {
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

	.whatsapp-float {
		position: fixed;
		bottom: 24px;
		right: 24px;
		width: 56px;
		height: 56px;
		background: #25d366;
		color: white;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
		box-shadow: 0 4px 12px rgba(37, 211, 102, 0.4);
		z-index: 999;
		transition: all 0.3s ease;

		&:hover {
			transform: scale(1.1);
			box-shadow: 0 6px 20px rgba(37, 211, 102, 0.6);
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
		border-top: 1px solid #e5e5e5;
	}

	.footer-container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 60px 32px 30px;
		display: grid;
		grid-template-columns: 2fr 1fr 1fr 1fr;
		gap: 48px;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
			gap: 32px;
			padding: 40px 16px 20px;
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
				width: 32px;
				height: 32px;
			}

			.brand-name {
				font-size: 20px;
				font-weight: 700;
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
			margin-top: 8px;

			a {
				display: flex;
				align-items: center;
				justify-content: center;
				width: 36px;
				height: 36px;
				background: white;
				border-radius: 50%;
				color: black;
				transition: all 0.3s ease;
				box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);

				&:hover {
					transform: translateY(-3px);
					box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
				}
			}
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

	.footer-bottom {
		max-width: 1200px;
		margin: 0 auto;
		padding: 24px 32px;
		border-top: 1px solid #e5e5e5;
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 14px;
		color: #666;

		@media (max-width: 768px) {
			flex-direction: column;
			gap: 12px;
			padding: 20px 16px;
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
