<script>
	import favicon from '$lib/assets/favicon.png';
	import logo from '$lib/assets/logo.png';
	import logoTransparent from '$lib/assets/logo-transparent.png';
	import logoFooter from '$lib/assets/logo-footer.png';
	import logoFooterTransparent from '$lib/assets/logo-footer-transparent.png';
	import '@fontsource/poppins';
	import Icon from '@iconify/svelte';
	import '../main.scss';
	let { children } = $props();

	let isDark = $state(false);
	let isRotating = $state(false);
	let isScrolled = $state(false);
	let isMobileMenuOpen = $state(false);
	let openMobileDropdowns = $state(new Set());

	function toggleMobileMenu() {
		isMobileMenuOpen = !isMobileMenuOpen;
		if (!isMobileMenuOpen) {
			openMobileDropdowns = new Set(); // Reset dropdowns when closing menu
		}
	}

	function toggleMobileDropdown(dropdown) {
		const newSet = new Set(openMobileDropdowns);
		if (newSet.has(dropdown)) {
			newSet.delete(dropdown);
		} else {
			newSet.add(dropdown);
		}
		openMobileDropdowns = newSet;
	}

	// Add this function
	function handleScroll() {
		isScrolled = window.scrollY > 50; // Adjust threshold as needed
	}

	// Add scroll listener in the $effect
	$effect(() => {
		initTheme();

		// Add scroll listener
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

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

<nav class="navbar-container" class:scrolled={isScrolled}>
	<div class="navbar-logo">
		<a href="/" class="home-link">
			<!-- <img src={logo} alt="Logo" class="logo" /> -->
			<img src={isDark ? logoTransparent : logo} alt="Logo" class="logo" />
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

		<button class="hamburger" onclick={toggleMobileMenu} aria-label="Toggle menu">
			<Icon icon="material-symbols:menu-rounded" width="24" height="24" />
		</button>
	</div>

	<!-- Mobile Menu Overlay -->
	{#if isMobileMenuOpen}
		<div class="mobile-menu-overlay" onclick={toggleMobileMenu}></div>
		<div class="mobile-menu">
			<div class="mobile-menu-header">
				<span class="mobile-menu-title">Menu</span>
				<button class="mobile-close" onclick={toggleMobileMenu} aria-label="Close menu">
					<Icon icon="material-symbols:close-rounded" width="24" height="24" />
				</button>
			</div>
			<ul>
				<li><a href="/" onclick={toggleMobileMenu}>Home</a></li>
				<li><a href="/about" onclick={toggleMobileMenu}>About</a></li>

				<li class="mobile-dropdown">
					<button
						class="mobile-dropdown-toggle"
						onclick={() => toggleMobileDropdown('services')}
						class:open={openMobileDropdowns.has('services')}
					>
						<span>Services</span>
						<Icon icon="mingcute:down-line" width="20" height="20" />
					</button>
					{#if openMobileDropdowns.has('services')}
						<ul class="mobile-submenu">
							<li>
								<a href="/services/planning-for-retirement" onclick={toggleMobileMenu}>
									<Icon icon="mdi:piggy-bank" width="18" height="18" />
									<span>Planning for Retirement</span>
								</a>
							</li>
							<li>
								<a href="/services/real-estate-consulting" onclick={toggleMobileMenu}>
									<Icon icon="mdi:home-city" width="18" height="18" />
									<span>Real Estate Consulting</span>
								</a>
							</li>
							<li>
								<a href="/services/asset-restructuring" onclick={toggleMobileMenu}>
									<Icon icon="mdi:shuffle" width="18" height="18" />
									<span>Asset Restructuring</span>
								</a>
							</li>
							<li>
								<a href="/services/selling-a-property" onclick={toggleMobileMenu}>
									<Icon icon="mdi:tag-multiple" width="18" height="18" />
									<span>Selling a Property</span>
								</a>
							</li>
							<li>
								<a href="/services/buying-a-property" onclick={toggleMobileMenu}>
									<Icon icon="mdi:shopping" width="18" height="18" />
									<span>Buying a Property</span>
								</a>
							</li>
							<li>
								<a href="/services/renting-a-property" onclick={toggleMobileMenu}>
									<Icon icon="mdi:key" width="18" height="18" />
									<span>Renting a Property</span>
								</a>
							</li>
						</ul>
					{/if}
				</li>

				<li><a href="/portfolio" onclick={toggleMobileMenu}>Portfolio</a></li>

				<li class="mobile-dropdown">
					<button
						class="mobile-dropdown-toggle"
						onclick={() => toggleMobileDropdown('resources')}
						class:open={openMobileDropdowns.has('resources')}
					>
						<span>Resources</span>
						<Icon icon="mingcute:down-line" width="20" height="20" />
					</button>
					{#if openMobileDropdowns.has('resources')}
						<ul class="mobile-submenu">
							<li>
								<a href="/about" onclick={toggleMobileMenu}>
									<Icon icon="mdi:information" width="18" height="18" />
									<span>About</span>
								</a>
							</li>
							<li>
								<a href="/portfolio" onclick={toggleMobileMenu}>
									<Icon icon="mdi:briefcase" width="18" height="18" />
									<span>Portfolio</span>
								</a>
							</li>
							<li>
								<a href="/reads" onclick={toggleMobileMenu}>
									<Icon icon="mdi:book-open" width="18" height="18" />
									<span>Featured Reads</span>
								</a>
							</li>
							<li>
								<a href="/testimonials" onclick={toggleMobileMenu}>
									<Icon icon="dashicons:testimonial" width="18" height="18" />
									<span>Testimonials</span>
								</a>
							</li>
							<li>
								<a
									href="https://www.edgeprop.sg/analytic/edgefairvalue/condominium"
									target="_blank"
									onclick={toggleMobileMenu}
								>
									<Icon icon="mdi:chart-line" width="18" height="18" />
									<span>Property Valuation</span>
								</a>
							</li>
							<li>
								<a href="/financial-calculator" onclick={toggleMobileMenu}>
									<Icon icon="mdi:calculator" width="18" height="18" />
									<span>Financial Calculator</span>
								</a>
							</li>
						</ul>
					{/if}
				</li>

				<li><a href="/water-concept" onclick={toggleMobileMenu}>WATER Concept</a></li>
				<li><a href="/contact" class="mobile-cta" onclick={toggleMobileMenu}>Contact Me</a></li>
			</ul>
		</div>
	{/if}
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
				<!-- <img src={logoFooter} alt="Logo" class="logo" /> -->
				<img src={isDark ? logoFooterTransparent : logoFooter} alt="Logo" class="logo" />
			</div>
			<p class="brand-description">
				Your trusted real estate partner. Specialising in portfolio upgrading and strategic property
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
		background-color: #f8f8f8;
		color: #333333;
	}

	/* Dark Mode */
	:global(html[data-theme='dark']) {
		color-scheme: dark;
	}

	:global(html[data-theme='dark']) :global(body) {
		background-color: #1a1a1a;
		color: #d0d0d0;
	}

	.navbar-container {
		position: sticky;
		top: -100px;
		z-index: 1000;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 16px 32px;
		background: transparent;
		border-bottom: 1px solid transparent;
		box-shadow: none;
		transition: all 0.3s ease;

		&.scrolled {
			top: 0;
			background: #f8f9fa;
			border-bottom: 1px solid #e0e0e0;
			box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
		}
	}

	:global(html[data-theme='dark']) .navbar-container {
		background: transparent;
		border: 1px solid transparent;
		border-bottom-color: transparent;
		box-shadow: none;

		&.scrolled {
			top: 0;
			background: #1a1a1a;
			border: 1px solid rgba(255, 255, 255, 0.12);
			border-bottom-color: rgba(255, 255, 255, 0.12);
			box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
		}
	}

	.navbar-logo {
		display: flex;
		align-items: center;
		gap: 12px;

		.logo {
			width: 150px;
			height: auto;

			@media (max-width: 768px) {
				width: 120px;
			}
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
				box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
				border-radius: 1rem;
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
					border-radius: 0.8rem;
					transition: all 0.3s ease;

					&:hover {
						background: #f0f0f0;
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
		color: #fff !important;
		box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3) !important;

		li a {
			color: #fff !important;

			&:hover {
				background: rgba(255, 255, 255, 0.1) !important;
				color: #f8f8f8 !important;
			}
		}
	}

	.nav-link {
		display: inline-flex;
		align-items: center;
		padding: 10px 16px;
		gap: 4px;
		color: black;
		text-decoration: none;
		position: relative;
		transition: all 0.3s ease;
		border-radius: 50px;

		&:hover {
			background: #f0f0f0;
		}

		&:hover :global(svg) {
			transform: rotate(180deg);
		}

		:global(svg) {
			transition: transform 0.3s ease;
		}
	}

	.dropdown:hover .nav-link :global(svg) {
		transform: rotate(180deg);
	}

	:global(html[data-theme='dark']) .nav-link {
		color: #fff;

		&:hover {
			background: rgba(255, 255, 255, 0.1);
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
		color: #fff;

		&:hover {
			background: rgba(255, 255, 255, 0.1);
		}
	}

	.cta-button {
		display: inline-block;
		padding: 10px 20px;
		background: transparent;
		color: #1a1a1a;
		border: 2px solid #1a1a1a;
		border-radius: 50px;
		font-weight: 600;
		font-size: 14px;
		text-decoration: none;
		cursor: pointer;
		transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
		letter-spacing: 0.5px;

		&:hover {
			transform: translateY(-4px);
			box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
		}

		@media (max-width: 768px) {
			.cta-button {
				padding: 6px 12px;
				font-size: 12px;
			}
		}
	}

	:global(html[data-theme='dark']) .cta-button {
		background: transparent;
		border: 2px solid #f8f8f8;
		color: #f8f8f8;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);

		&:hover {
			transform: translateY(-4px);
			box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
		}
	}

	.hamburger {
		display: none;
		background: transparent;
		border: none;
		color: #333;
		cursor: pointer;
		padding: 8px;
		border-radius: 8px;
		transition: background 0.3s ease;

		&:hover {
			background: #f0f0f0;
		}

		@media (max-width: 768px) {
			display: flex;
			align-items: center;
			justify-content: center;
		}
	}

	:global(html[data-theme='dark']) .hamburger {
		color: #fff;

		&:hover {
			background: rgba(255, 255, 255, 0.1);
		}
	}

	.desktop-only {
		@media (max-width: 768px) {
			display: none;
		}
	}

	.mobile-menu-overlay {
		display: none;

		@media (max-width: 768px) {
			display: block;
			position: fixed;
			top: 0;
			left: 0;
			right: 0;
			bottom: 0;
			background: rgba(0, 0, 0, 0.5);
			z-index: 998;
			animation: fadeIn 0.3s ease;
		}
	}

	.mobile-menu {
		display: none;
		padding: 24px;
		z-index: 999;

		.mobile-menu-header {
			display: flex;
			justify-content: space-between;
			align-items: center;
			margin-bottom: 24px;
			padding-bottom: 16px;
			border-bottom: 1px solid #e0e0e0;

			.mobile-menu-title {
				font-size: 20px;
				font-weight: 600;
				color: #333;
			}

			.mobile-close {
				display: flex;
				align-items: center;
				justify-content: center;
				background: transparent;
				border: none;
				color: #333;
				cursor: pointer;
				padding: 8px;
				border-radius: 8px;
				transition: background 0.3s ease;

				&:hover {
					background: #f0f0f0;
				}
			}
		}

		@media (max-width: 768px) {
			display: block;
			position: fixed;
			top: 0;
			right: 0;
			width: 280px;
			height: 100vh;
			background: #fff;
			z-index: 999;
			padding: 40px 24px 24px;
			overflow-y: auto;
			box-shadow: -4px 0 24px rgba(0, 0, 0, 0.15);
			animation: slideIn 0.3s ease;
			// Add smooth scrolling
			-webkit-overflow-scrolling: touch;

			ul {
				list-style: none;
				padding: 0;
				margin: 0;
				display: flex;
				flex-direction: column;
				gap: 4px;

				li {
					a {
						display: flex;
						align-items: center;
						gap: 12px;
						padding: 14px 16px;
						color: #333;
						text-decoration: none;
						border-radius: 12px;
						transition: all 0.3s ease;
						font-weight: 500;

						&:hover {
							background: #f0f0f0;
						}

						&.mobile-cta {
							margin-top: 16px;
							background: #1a1a1a;
							color: #fff;
							text-align: center;
							justify-content: center;
							font-weight: 600;

							&:hover {
								background: #333;
							}
						}
					}
				}
			}

			.mobile-dropdown {
				.mobile-dropdown-toggle {
					display: flex;
					align-items: center;
					justify-content: space-between;
					width: 100%;
					padding: 14px 16px;
					color: #333;
					font-weight: 500;
					background: transparent;
					border: none;
					border-radius: 12px;
					cursor: pointer;
					transition: all 0.3s ease;
					font-family: 'Poppins', sans-serif;
					font-size: 1rem;

					&:hover {
						background: #f0f0f0;
					}

					:global(svg) {
						transition: transform 0.3s ease;
					}

					&.open :global(svg) {
						transform: rotate(180deg);
					}
				}

				.mobile-submenu {
					padding-left: 16px;
					margin-top: 4px;
					overflow: hidden;
					animation: slideDown 0.3s ease;

					li a {
						padding: 10px 16px;
						font-size: 14px;
						font-weight: 400;
					}
				}
			}
		}
	}

	:global(html[data-theme='dark']) .mobile-menu {
		background: #1a1a1a;
		box-shadow: -4px 0 24px rgba(0, 0, 0, 0.5);

		.mobile-menu-header {
			border-bottom-color: rgba(255, 255, 255, 0.1);

			.mobile-menu-title {
				color: #fff;
			}

			.mobile-close {
				color: #fff;

				&:hover {
					background: rgba(255, 255, 255, 0.1);
				}
			}
		}

		ul li a {
			color: #fff;

			&:hover {
				background: rgba(255, 255, 255, 0.1);
			}

			&.mobile-cta {
				background: #fff;
				color: #1a1a1a;

				&:hover {
					background: #f0f0f0;
				}
			}
		}

		.mobile-dropdown {
			.mobile-dropdown-toggle {
				color: #fff;

				&:hover {
					background: rgba(255, 255, 255, 0.1);
				}
			}
		}
	}

	@keyframes slideDown {
		from {
			opacity: 0;
			max-height: 0;
		}
		to {
			opacity: 1;
			max-height: 500px;
		}
	}

	@keyframes slideIn {
		from {
			transform: translateX(100%);
		}
		to {
			transform: translateX(0);
		}
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
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
		background: #f8f9fa;
		color: #333;
		border-top: 1px solid #fff;
	}

	:global(html[data-theme='dark']) .footer {
		background: transparent;
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
				background: #fff;
				border: 1px solid #e0e0e0;
				border-radius: 50%;
				color: #1a1a1a;
				transition: all 0.3s ease;
				box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);

				&:hover {
					transform: translateY(-4px);
					background: #fafafa;
					box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
				}
			}

			@media (max-width: 768px) {
				gap: 8px;
			}
		}
	}

	:global(html[data-theme='dark']) .footer-brand .brand-description {
		color: #aaa;
	}

	:global(html[data-theme='dark']) .footer-brand .social-links a {
		background: rgba(238, 231, 222, 0.12);
		border: 1px solid rgba(255, 255, 255, 0.12);
		color: #d0d0d0;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);

		&:hover {
			background: rgba(238, 231, 222, 0.18);
			border-color: rgba(255, 255, 255, 0.2);
			box-shadow: 0 4px 8px rgba(0, 0, 0, 0.4);
		}
	}

	.footer-column {
		h3 {
			font-size: 1rem;
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
			color: #fff;
		}

		ul li a {
			color: #aaa;

			&:hover {
				color: #fff;
			}
		}
	}

	.footer-bottom {
		max-width: 1200px;
		margin: 0 auto;
		padding: 24px 32px;
		border-top: 1px solid #fff;
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
				color: #fff;
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

		.navbar-logo {
			flex: 1;
		}
	}
</style>
