<script>
	import { onMount } from 'svelte';

	let activeCalculator = $state('mortgage');

	// Mortgage Calculator State
	let purchasePrice = $state('');
	let ltv = $state('75');
	let loanTenure = $state('25');
	let interestRate = $state('3.5');
	let mortgageResult = $state(null);

	// Sales Proceeds Calculator State
	let salesPrice = $state('');
	let outstandingLoan = $state('');
	let cpfRefunds = $state('');
	let legalFees = $state('3,000');
	let ssd = $state('0');
	let proceedsResult = $state(null);

	let calculatorsVisible = $state(false);

	onMount(() => {
		const observer = new IntersectionObserver(
			(entries) => {
				entries.forEach((entry) => {
					if (entry.isIntersecting) {
						calculatorsVisible = true;
					}
				});
			},
			{ threshold: 0.1 }
		);

		const section = document.querySelector('.calculators-section');
		if (section) observer.observe(section);

		return () => observer.disconnect();
	});

	function formatMoney(amount) {
		return amount.toLocaleString('en-SG', {
			style: 'currency',
			currency: 'SGD',
			minimumFractionDigits: 2,
			maximumFractionDigits: 2
		});
	}

	function calculateMortgage() {
		// const price = parseFloat(purchasePrice);
		const price = parseFloat(purchasePrice.replace(/,/g, ''));
		const ltvDecimal = parseFloat(ltv) / 100;
		const loanTenureMonths = parseFloat(loanTenure) * 12;
		const interestRateMonthly = parseFloat(interestRate) / 100 / 12;

		if (!price || !ltvDecimal || !loanTenureMonths || !interestRateMonthly) {
			mortgageResult = null;
			return;
		}

		const loanAmount = price * ltvDecimal;
		const monthlyRepayment =
			(loanAmount * interestRateMonthly) /
			(1 - Math.pow(1 + interestRateMonthly, -loanTenureMonths));
		const totalRepayment = monthlyRepayment * loanTenureMonths;
		const totalInterest = totalRepayment - loanAmount;
		const monthlyPrincipal = loanAmount / loanTenureMonths;
		const monthlyInterest = monthlyRepayment - monthlyPrincipal;

		mortgageResult = {
			loanAmount,
			monthlyRepayment,
			monthlyPrincipal,
			monthlyInterest,
			totalRepayment,
			totalInterest
		};
	}

	function calculateProceeds() {
		// const sales = parseFloat(salesPrice);
		// const loan = parseFloat(outstandingLoan) || 0;
		// const cpf = parseFloat(cpfRefunds) || 0;
		// const legal = parseFloat(legalFees) || 0;
		// const ssdAmount = parseFloat(ssd) || 0;
		const sales = parseFloat(salesPrice.replace(/,/g, ''));
		const loan = parseFloat((outstandingLoan || '0').replace(/,/g, ''));
		const cpf = parseFloat((cpfRefunds || '0').replace(/,/g, ''));
		const legal = parseFloat((legalFees || '0').replace(/,/g, ''));
		const ssdAmount = parseFloat((ssd || '0').replace(/,/g, ''));

		if (!sales) {
			proceedsResult = null;
			return;
		}

		const cashProceeds = sales - loan - cpf - legal - ssdAmount;

		proceedsResult = {
			salesPrice: sales,
			outstandingLoan: loan,
			cpfRefunds: cpf,
			legalFees: legal,
			ssd: ssdAmount,
			cashProceeds
		};
	}

	function resetMortgage() {
		purchasePrice = '';
		ltv = '75';
		loanTenure = '25';
		interestRate = '3.5';
		mortgageResult = null;
	}

	function resetProceeds() {
		salesPrice = '';
		outstandingLoan = '';
		cpfRefunds = '';
		legalFees = '3,000';
		ssd = '0';
		proceedsResult = null;
	}
</script>

<div class="calculators-page">
	<!-- Hero Section -->
	<section class="hero">
		<div class="container">
			<h1 class="hero-title">Financial Calculators</h1>
			<p class="hero-subtitle">Make informed property decisions with our easy-to-use calculators</p>
		</div>
	</section>

	<!-- Calculators Section -->
	<section class="calculators-section">
		<div class="container">
			<!-- Calculator Toggle -->
			<div class="calculator-toggle" class:visible={calculatorsVisible}>
				<button
					class="toggle-btn"
					class:active={activeCalculator === 'mortgage'}
					onclick={() => (activeCalculator = 'mortgage')}
				>
					Mortgage Calculator
				</button>
				<button
					class="toggle-btn"
					class:active={activeCalculator === 'proceeds'}
					onclick={() => (activeCalculator = 'proceeds')}
				>
					Sales Proceeds Calculator
				</button>
			</div>

			<!-- Mortgage Calculator -->
			{#if activeCalculator === 'mortgage'}
				<div class="calculator-container" class:visible={calculatorsVisible}>
					<div class="calculator-grid">
						<div class="calculator-form">
							<h2>Mortgage Calculator</h2>
							<p class="calculator-description">
								Calculate your monthly mortgage payments and total interest over the loan tenure.
							</p>

							<div class="form-group">
								<label for="purchasePrice">Purchase Price (S$)</label>
								<input
									type="text"
									id="purchasePrice"
									bind:value={purchasePrice}
									placeholder="e.g., 800,000"
									oninput={(e) => {
										e.target.value = e.target.value
											.replace(/[^\d]/g, '')
											.replace(/\B(?=(\d{3})+(?!\d))/g, ',');
										purchasePrice = e.target.value;
										calculateMortgage();
									}}
								/>
							</div>

							<div class="form-group">
								<label for="ltv">Loan-to-Value Ratio (%)</label>
								<div class="input-with-display">
									<input
										type="range"
										id="ltv"
										bind:value={ltv}
										min="5"
										max="95"
										step="1"
										oninput={calculateMortgage}
									/>
									<input
										type="number"
										bind:value={ltv}
										min="5"
										max="95"
										step="1"
										class="range-input-box"
										oninput={calculateMortgage}
									/>
									<span class="range-label">%</span>
								</div>
							</div>

							<div class="form-group">
								<label for="loanTenure">Loan Tenure (Years)</label>
								<div class="input-with-display">
									<input
										type="range"
										id="loanTenure"
										bind:value={loanTenure}
										min="5"
										max="35"
										step="1"
										oninput={calculateMortgage}
									/>
									<input
										type="number"
										bind:value={loanTenure}
										min="5"
										max="35"
										step="1"
										class="range-input-box"
										oninput={calculateMortgage}
									/>
									<span class="range-label">years</span>
								</div>
							</div>

							<div class="form-group">
								<label for="interestRate">Interest Rate (% p.a.)</label>
								<input
									type="number"
									id="interestRate"
									bind:value={interestRate}
									step="0.1"
									placeholder="e.g., 3.5"
									oninput={calculateMortgage}
								/>
							</div>

							<button class="reset-btn" onclick={resetMortgage}>Reset</button>
						</div>

						<div class="calculator-results">
							{#if mortgageResult}
								<div class="result-card primary">
									<h3>Loan Amount</h3>
									<p class="result-value">{formatMoney(mortgageResult.loanAmount)}</p>
								</div>

								<div class="result-card">
									<h3>Monthly Repayment</h3>
									<p class="result-value">{formatMoney(mortgageResult.monthlyRepayment)}</p>
									<div class="result-breakdown">
										<div class="breakdown-item">
											<span>Principal</span>
											<span>{formatMoney(mortgageResult.monthlyPrincipal)}</span>
										</div>
										<div class="breakdown-item">
											<span>Interest</span>
											<span>{formatMoney(mortgageResult.monthlyInterest)}</span>
										</div>
									</div>
								</div>

								<div class="result-card">
									<h3>Total Repayment</h3>
									<p class="result-value">{formatMoney(mortgageResult.totalRepayment)}</p>
								</div>

								<div class="result-card">
									<h3>Total Interest Paid</h3>
									<p class="result-value highlight">{formatMoney(mortgageResult.totalInterest)}</p>
								</div>
							{:else}
								<div class="empty-state">
									<svg
										width="120"
										height="120"
										viewBox="0 0 24 24"
										fill="none"
										stroke="currentColor"
										stroke-width="1.5"
									>
										<path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
										<polyline points="9 22 9 12 15 12 15 22"></polyline>
									</svg>
									<p>Enter your property details to calculate mortgage payments</p>
								</div>
							{/if}
						</div>
					</div>
				</div>
			{/if}

			<!-- Sales Proceeds Calculator -->
			{#if activeCalculator === 'proceeds'}
				<div class="calculator-container" class:visible={calculatorsVisible}>
					<div class="calculator-grid">
						<div class="calculator-form">
							<h2>Sales Proceeds Calculator</h2>
							<p class="calculator-description">
								Estimate your net cash proceeds after selling your property.
							</p>

							<div class="form-group">
								<label for="salesPrice">Sales Price (S$)</label>
								<input
									type="text"
									id="salesPrice"
									bind:value={salesPrice}
									placeholder="e.g., 900,000"
									oninput={(e) => {
										e.target.value = e.target.value
											.replace(/[^\d]/g, '')
											.replace(/\B(?=(\d{3})+(?!\d))/g, ',');
										salesPrice = e.target.value;
										calculateProceeds();
									}}
								/>
							</div>

							<div class="form-group">
								<label for="outstandingLoan">Outstanding Loan (S$)</label>
								<input
									type="text"
									id="outstandingLoan"
									bind:value={outstandingLoan}
									placeholder="e.g., 500,000"
									oninput={(e) => {
										e.target.value = e.target.value
											.replace(/[^\d]/g, '')
											.replace(/\B(?=(\d{3})+(?!\d))/g, ',');
										outstandingLoan = e.target.value;
										calculateProceeds();
									}}
								/>
							</div>

							<div class="form-group">
								<label for="cpfRefunds">CPF Refunds (S$)</label>
								<input
									type="text"
									id="cpfRefunds"
									bind:value={cpfRefunds}
									placeholder="e.g., 150,000"
									oninput={(e) => {
										e.target.value = e.target.value
											.replace(/[^\d]/g, '')
											.replace(/\B(?=(\d{3})+(?!\d))/g, ',');
										cpfRefunds = e.target.value;
										calculateProceeds();
									}}
								/>
								<small>Amount to be refunded to CPF (principal + accrued interest)</small>
							</div>

							<div class="form-group">
								<label for="legalFees">Legal Fees (S$)</label>
								<input
									type="text"
									id="legalFees"
									bind:value={legalFees}
									placeholder="e.g., 3,000"
									oninput={(e) => {
										e.target.value = e.target.value
											.replace(/[^\d]/g, '')
											.replace(/\B(?=(\d{3})+(?!\d))/g, ',');
										legalFees = e.target.value;
										calculateProceeds();
									}}
								/>
							</div>

							<div class="form-group">
								<label for="ssd">Seller's Stamp Duty (S$)</label>
								<input
									type="text"
									id="ssd"
									bind:value={ssd}
									placeholder="e.g., 0"
									oninput={(e) => {
										e.target.value = e.target.value
											.replace(/[^\d]/g, '')
											.replace(/\B(?=(\d{3})+(?!\d))/g, ',');
										ssd = e.target.value;
										calculateProceeds();
									}}
								/>
								<small>If applicable (based on holding period)</small>
							</div>

							<button class="reset-btn" onclick={resetProceeds}>Reset</button>
						</div>

						<div class="calculator-results">
							{#if proceedsResult}
								<div class="result-card breakdown-card">
									<h3>Sales Breakdown</h3>
									<div class="breakdown-list">
										<div class="breakdown-row sales">
											<span>Sales Price</span>
											<span>{formatMoney(proceedsResult.salesPrice)}</span>
										</div>
										<div class="breakdown-row deduction">
											<span>Outstanding Loan</span>
											<span>-{formatMoney(proceedsResult.outstandingLoan)}</span>
										</div>
										<div class="breakdown-row deduction">
											<span>CPF Refunds</span>
											<span>-{formatMoney(proceedsResult.cpfRefunds)}</span>
										</div>
										<div class="breakdown-row deduction">
											<span>Legal Fees</span>
											<span>-{formatMoney(proceedsResult.legalFees)}</span>
										</div>
										{#if proceedsResult.ssd > 0}
											<div class="breakdown-row deduction">
												<span>Seller's Stamp Duty</span>
												<span>-{formatMoney(proceedsResult.ssd)}</span>
											</div>
										{/if}
									</div>
								</div>

								<div class="result-card primary large">
									<h3>Estimated Cash Proceeds</h3>
									<p class="result-value big">{formatMoney(proceedsResult.cashProceeds)}</p>
									{#if proceedsResult.cashProceeds < 0}
										<p class="warning-text">
											⚠️ You may need additional cash to complete this sale
										</p>
									{/if}
								</div>
							{:else}
								<div class="empty-state">
									<svg
										width="120"
										height="120"
										viewBox="0 0 24 24"
										fill="none"
										stroke="currentColor"
										stroke-width="1.5"
									>
										<rect x="2" y="5" width="20" height="14" rx="2"></rect>
										<line x1="2" y1="10" x2="22" y2="10"></line>
									</svg>
									<p>Enter your sales details to estimate cash proceeds</p>
								</div>
							{/if}
						</div>
					</div>
				</div>
			{/if}

			<!-- Disclaimer -->
			<div class="disclaimer" class:visible={calculatorsVisible}>
				<p>
					<strong>Disclaimer:</strong> These calculators provide estimates for informational purposes
					only. Actual figures may vary based on specific circumstances, bank policies, and market conditions.
					Please consult with a qualified professional for personalised advice.
				</p>
			</div>
		</div>
	</section>
</div>

<style>
	* {
		box-sizing: border-box;
	}

	.calculators-page {
		min-height: 100vh;
		background: #f8f8f8;
	}

	.container {
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 20px;
	}

	/* Hero Section */
	.hero {
		background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
		color: #000;
		padding: 80px 0 60px;
		text-align: center;
	}

	.hero-title {
		font-size: 2.5rem;
		font-weight: 700;
		margin: 0 0 16px 0;
		line-height: 1.2;
	}

	/* DARK THEME - HERO SECTION */
	:global(html[data-theme='dark']) .hero {
		background: linear-gradient(135deg, #1a1a1a 0%, #2a2a2a 100%);
		color: #ffffff;
	}

	:global(html[data-theme='dark']) .hero-title {
		color: #ffffff;
	}

	:global(html[data-theme='dark']) .hero-subtitle {
		color: #b0b0c0;
		opacity: 0.9;
	}

	@media (max-width: 768px) {
		.hero-title {
			font-size: 1.75rem;
		}
	}

	.hero-subtitle {
		font-size: 20px;
		color: #666;
		max-width: 600px;
		margin: 0 auto;
		opacity: 0.9;
	}

	@media (max-width: 768px) {
		.hero-subtitle {
			font-size: 0.95rem;
			max-width: 400px;
		}
	}

	/* Calculator Toggle */
	.calculator-toggle {
		display: flex;
		justify-content: center;
		gap: 16px;
		padding: 40px 0;
		opacity: 0;
		transform: translateY(20px);
		transition: all 0.6s ease;
	}

	.calculator-toggle.visible {
		opacity: 1;
		transform: translateY(0);
	}

	.toggle-btn {
		padding: 14px 32px;
		background: #fff;
		border: 1px solid #e0e0e0;
		border-radius: 1rem;
		font-size: 1rem;
		font-weight: 600;
		cursor: pointer;
		transition: all 0.3s ease;
		color: #1a1a1a;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	}

	@media (max-width: 768px) {
		.toggle-btn {
			padding: 10px 20px;
			font-size: 0.9rem;
		}
	}

	.toggle-btn:hover {
		background: #f5f5f5;
		border-color: #d0d0d0;
		transform: translateY(-2px);
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.12);
	}

	.toggle-btn.active {
		background: #1a1a1a;
		color: white;
		border-color: #1a1a1a;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
	}

	/* Calculator Container */
	.calculators-section {
		padding: 0 0 100px;
	}

	.calculator-container {
		opacity: 0;
		transform: translateY(30px);
		transition: all 0.6s ease;
	}

	.calculator-container.visible {
		opacity: 1;
		transform: translateY(0);
	}

	.calculator-grid {
		display: grid;
		grid-template-columns: 45% 1fr;
		gap: 48px;
		background: #fff;
		padding: 48px;
		border-radius: 1.5rem;
		border: 1px solid #e0e0e0;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.08);
	}

	@media (max-width: 968px) {
		.calculator-grid {
			grid-template-columns: 1fr;
			gap: 40px;
			padding: 32px;
		}
	}

	@media (max-width: 640px) {
		.calculator-grid {
			padding: 24px;
		}

		.hero-title {
			font-size: 36px;
		}

		.hero-subtitle {
			font-size: 18px;
		}
	}

	/* Form Styles */
	.calculator-form h2 {
		font-size: 1.5rem;
		font-weight: 700;
		margin: 0 0 12px 0;
	}

	@media (max-width: 768px) {
		.calculator-form h2 {
			font-size: 1.2rem;
		}
	}

	.calculator-description {
		font-size: 1rem;
		color: #666;
		margin: 0 0 32px 0;
		line-height: 1.6;
	}

	.form-group {
		margin-bottom: 28px;
	}

	.form-group label {
		display: block;
		font-weight: 600;
		margin-bottom: 8px;
		color: #333;
	}

	.form-group input[type='number'],
	.form-group input[type='text'] {
		width: 100%;
		padding: 12px 16px;
		background: white;
		border: 1px solid #d0d0d0;
		border-radius: 0.8rem;
		font-size: 1rem;
		transition: all 0.3s ease;
	}

	.form-group input[type='number']:focus,
	.form-group input[type='text']:focus {
		outline: none;
		background: white;
		border-color: #1a1a1a;
		box-shadow: 0 0 0 3px rgba(26, 26, 46, 0.1);
	}

	.form-group input[type='range'] {
		width: 100%;
		height: 6px;
		border-radius: 5px;
		background: rgba(0, 0, 0, 0.1);
		outline: none;
		-webkit-appearance: none;
	}

	.form-group input[type='range']::-webkit-slider-thumb {
		-webkit-appearance: none;
		appearance: none;
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background: linear-gradient(135deg, #1a1a1a 0%, #333 100%);
		cursor: pointer;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
		transition: all 0.2s ease;
	}

	.form-group input[type='range']::-webkit-slider-thumb:hover {
		transform: scale(1.15);
		box-shadow: 0 6px 16px rgba(0, 0, 0, 0.3);
	}

	.form-group input[type='range']::-moz-range-thumb {
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background: linear-gradient(135deg, #1a1a1a 0%, #333 100%);
		cursor: pointer;
		border: none;
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.2);
		transition: all 0.2s ease;
	}

	:global(html[data-theme='dark']) .form-group input[type='range']::-webkit-slider-thumb {
		background: linear-gradient(135deg, #ffffff 0%, #e0e0e0 100%);
	}

	:global(html[data-theme='dark']) .form-group input[type='range']::-moz-range-thumb {
		background: linear-gradient(135deg, #ffffff 0%, #e0e0e0 100%);
	}

	.input-with-display {
		display: flex;
		align-items: center;
		gap: 16px;
	}

	.range-input-box {
		width: 80px !important;
		padding: 8px 12px;
		background: white !important;
		border: 1px solid #d0d0d0 !important;
		border-radius: 0.8rem !important;
		font-size: 16px;
		text-align: center;
		transition: all 0.3s ease;
	}

	.range-input-box:focus {
		outline: none;
		background: white !important;
		border-color: #1a1a1a !important;
	}

	.range-label {
		font-weight: 600;
		color: #666;
		min-width: 20px;
	}

	.form-group small {
		display: block;
		margin-top: 6px;
		color: #999;
		font-size: 13px;
	}

	.reset-btn {
		width: 100%;
		padding: 10px 20px;
		background: transparent;
		color: #1a1a1a;
		border: 2px solid #1a1a1a;
		border-radius: 0.75rem;
		font-size: 1rem;
		font-weight: 600;
		cursor: pointer;
		transition: all 0.3s ease;
		margin-top: 12px;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
		font-family: 'Poppins', sans-serif;
	}

	.reset-btn:hover {
		border-color: #444;
		transform: translateY(-2px);
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.25);
	}

	/* Results Styles */
	.calculator-results {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	.result-card {
		background: white;
		padding: 24px;
		border-radius: 1rem;
		border: 1px solid #e0e0e0;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.06);
	}

	.result-card.primary {
		background: #1a1a1a;
		color: white;
		border: 1px solid #1a1a1a;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.15);
	}

	.result-card.large {
		padding: 32px;
	}

	.result-card h3 {
		font-size: 14px;
		font-weight: 600;
		margin: 0 0 12px 0;
		text-transform: uppercase;
		letter-spacing: 0.5px;
		opacity: 0.8;
	}

	.result-card.primary h3 {
		opacity: 0.9;
	}

	.result-value {
		font-size: 32px;
		font-weight: 700;
		margin: 0;
		color: #1a1a1a;
	}

	.result-value.big {
		font-size: 42px;
	}

	.result-card.primary .result-value {
		color: white;
	}

	.result-value.highlight {
		color: #d32f2f;
	}

	.result-breakdown {
		margin-top: 16px;
		padding-top: 16px;
		border-top: 1px solid #e0e0e0;
	}

	.breakdown-item {
		display: flex;
		justify-content: space-between;
		padding: 8px 0;
		font-size: 15px;
	}

	.breakdown-item span:first-child {
		color: #666;
	}

	.breakdown-item span:last-child {
		font-weight: 600;
	}

	/* .breakdown-card {
		background: linear-gradient(135deg, rgba(255, 255, 255, 0.9) 0%, rgba(240, 240, 245, 0.8) 100%);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
		border: 1.5px solid rgba(255, 255, 255, 0.6);
		box-shadow:
			0 4px 15px rgba(0, 0, 0, 0.08),
			inset -1px -1px 3px rgba(0, 0, 0, 0.05),
			inset 1px 1px 3px rgba(255, 255, 255, 0.8);
	} */

	.breakdown-card {
		background: white;
		border: 1px solid #e0e0e0;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.06);
	}

	.breakdown-list {
		margin-top: 16px;
	}

	.breakdown-row {
		display: flex;
		justify-content: space-between;
		padding: 12px 0;
		border-bottom: 1px solid #f0f0f0;
		font-size: 15px;
	}

	.breakdown-row:last-child {
		border-bottom: none;
	}

	.breakdown-row.sales span:last-child {
		font-weight: 700;
		color: #2e7d32;
	}

	.breakdown-row.deduction span:last-child {
		color: #d32f2f;
		font-weight: 600;
	}

	.warning-text {
		margin: 16px 0 0 0;
		padding: 12px;
		background: rgba(255, 152, 0, 0.1);
		border-radius: 0.25rem;
		color: #f57c00;
		font-size: 14px;
		font-weight: 600;
	}

	/* Empty State */
	.empty-state {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 100%;
		min-height: 400px;
		text-align: center;
		color: #999;
	}

	.empty-state svg {
		margin-bottom: 24px;
		opacity: 0.3;
	}

	.empty-state p {
		font-size: 16px;
		margin: 0;
		max-width: 300px;
	}

	/* Disclaimer */
	/* .disclaimer {
		margin-top: 40px;
		padding: 24px;
		background: linear-gradient(
			135deg,
			rgba(255, 255, 255, 0.85) 0%,
			rgba(245, 245, 250, 0.75) 100%
		);
		backdrop-filter: blur(8px);
		-webkit-backdrop-filter: blur(8px);
		border-radius: 0.25rem;
		border-left: 4px solid #ff9800;
		opacity: 0;
		transform: translateY(20px);
		transition: all 0.6s ease;
		transition-delay: 0.3s;
		box-shadow:
			0 4px 15px rgba(0, 0, 0, 0.05),
			inset -1px -1px 2px rgba(0, 0, 0, 0.03),
			inset 1px 1px 2px rgba(255, 255, 255, 0.7);
	} */

	.disclaimer {
		margin-top: 40px;
		padding: 24px;
		background: #fff;
		border-radius: 1rem;
		border-left: 4px solid #ff9800;
		opacity: 0;
		transform: translateY(20px);
		transition: all 0.6s ease;
		transition-delay: 0.3s;
		box-shadow: none;
	}

	.disclaimer.visible {
		opacity: 1;
		transform: translateY(0);
	}

	.disclaimer p {
		margin: 0;
		font-size: 14px;
		line-height: 1.6;
		color: #666;
	}

	.disclaimer strong {
		color: #333;
	}

	/* DARK THEME - BACKGROUND */
	:global(html[data-theme='dark']) .calculators-page {
		background: #1a1a1a;
	}

	/* DARK THEME - TOGGLE BUTTONS */
	:global(html[data-theme='dark']) .toggle-btn {
		background: rgba(60, 60, 80, 0.5);
		border-color: rgba(255, 255, 255, 0.15);
		color: #b0b0c0;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.4);
	}

	:global(html[data-theme='dark']) .toggle-btn:hover {
		background: rgba(70, 70, 90, 0.6);
		border-color: rgba(255, 255, 255, 0.2);
		box-shadow: 0 4px 6px rgba(0, 0, 0, 0.5);
	}

	:global(html[data-theme='dark']) .toggle-btn.active {
		background: linear-gradient(135deg, #64748b 0%, #475569 100%);
		border-color: #64748b;
		color: #ffffff;
		box-shadow: 0 2px 8px rgba(100, 116, 139, 0.35);
	}

	:global(html[data-theme='dark']) .toggle-btn.active:hover {
		box-shadow:
			0 12px 40px rgba(0, 0, 0, 0.6),
			inset -1px -1px 3px rgba(0, 0, 0, 0.6),
			inset 1px 1px 3px rgba(255, 255, 255, 0.15);
	}

	/* DARK THEME - CALCULATOR GRID */
	:global(html[data-theme='dark']) .calculator-grid {
		background: #1a1a1a;
		border: 1px solid rgba(255, 255, 255, 0.12);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
	}

	/* DARK THEME - FORM LABELS & TEXT */
	:global(html[data-theme='dark']) .calculator-form h2 {
		color: #e8e8f0;
	}

	:global(html[data-theme='dark']) .calculator-description {
		color: #b0b0c0;
	}

	:global(html[data-theme='dark']) .form-group label {
		color: #d0d0d0;
	}

	:global(html[data-theme='dark']) .form-group small {
		color: #808090;
	}

	/* DARK THEME - FORM INPUTS */
	:global(html[data-theme='dark']) .form-group input[type='number'],
	:global(html[data-theme='dark']) .form-group input[type='text'] {
		background: #2a2a2a;
		border-color: #3a3a3a;
		color: #fff;
	}

	:global(html[data-theme='dark']) .form-group input[type='number']:focus,
	:global(html[data-theme='dark']) .form-group input[type='text']:focus {
		background: #4a4a4a;
		border-color: #6a6a6a;
	}

	:global(html[data-theme='dark']) .form-group input[type='range'] {
		background: rgba(0, 0, 0, 0.3);
	}

	:global(html[data-theme='dark']) .range-input-box {
		background: #2a2a2a !important;
		border-color: #3a3a3a !important;
		color: #fff;
	}

	:global(html[data-theme='dark']) .range-input-box:focus {
		background: #4a4a4a !important;
		border-color: #6a6a6a !important;
	}

	:global(html[data-theme='dark']) .range-label {
		color: #a0a0b0;
	}

	/* DARK THEME - RESET BUTTON */
	:global(html[data-theme='dark']) .reset-btn {
		background: transparent;
		color: #e8e8f0;
		border: 2px solid #e8e8f0;
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.4);
	}

	:global(html[data-theme='dark']) .reset-btn:hover {
		box-shadow: 0 4px 12px rgba(0, 0, 0, 0.5);
	}

	/* DARK THEME - RESULT CARDS */
	:global(html[data-theme='dark']) .result-card {
		background: rgba(238, 231, 222, 0.12);
		border: 1px solid rgba(255, 255, 255, 0.12);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
		color: #d0d0d0;
	}

	:global(html[data-theme='dark']) .result-card.primary {
		background: rgba(100, 110, 140, 0.25);
		border-color: rgba(255, 255, 255, 0.15);
		box-shadow: 0 2px 8px rgba(0, 0, 0, 0.4);
	}

	:global(html[data-theme='dark']) .result-card.primary h3 {
		color: #d0d0d0;
	}

	:global(html[data-theme='dark']) .result-value {
		color: #e8e8f0;
	}

	:global(html[data-theme='dark']) .result-value.highlight {
		color: #ff6b6b;
	}

	:global(html[data-theme='dark']) .result-breakdown {
		border-top-color: rgba(255, 255, 255, 0.1);
	}

	:global(html[data-theme='dark']) .breakdown-item span:first-child {
		color: #a0a0b0;
	}

	:global(html[data-theme='dark']) .breakdown-item span:last-child {
		color: #d0d0d0;
	}

	/* DARK THEME - BREAKDOWN CARD */
	/* :global(html[data-theme='dark']) .breakdown-card {
		background: linear-gradient(
			135deg,
			rgba(238, 231, 222, 0.12) 0%,
			rgba(238, 231, 222, 0.04) 100%
		);
		backdrop-filter: blur(10px);
		-webkit-backdrop-filter: blur(10px);
		border: 1.5px solid rgba(255, 255, 255, 0.12);
		box-shadow:
			0 4px 15px rgba(0, 0, 0, 0.3),
			inset -1px -1px 3px rgba(0, 0, 0, 0.3),
			inset 1px 1px 3px rgba(255, 255, 255, 0.08);
	} */

	:global(html[data-theme='dark']) .breakdown-card {
		background: rgba(238, 231, 222, 0.12);
		border: 1px solid rgba(255, 255, 255, 0.12);
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
	}

	:global(html[data-theme='dark']) .breakdown-list {
		color: #d0d0d0;
	}

	:global(html[data-theme='dark']) .breakdown-row {
		border-bottom-color: rgba(255, 255, 255, 0.05);
		color: #d0d0d0;
	}

	:global(html[data-theme='dark']) .breakdown-row.sales span:last-child {
		color: #6bff6b;
	}

	:global(html[data-theme='dark']) .breakdown-row.deduction span:last-child {
		color: #ff8888;
	}

	/* DARK THEME - WARNING TEXT */
	:global(html[data-theme='dark']) .warning-text {
		background: rgba(255, 152, 0, 0.15);
		color: #ffb74d;
	}

	/* DARK THEME - EMPTY STATE */
	:global(html[data-theme='dark']) .empty-state {
		color: #606070;
	}

	:global(html[data-theme='dark']) .empty-state svg {
		color: #505060;
	}

	/* DARK THEME - DISCLAIMER */
	/* :global(html[data-theme='dark']) .disclaimer {
		background: linear-gradient(135deg, rgba(70, 75, 100, 0.35) 0%, rgba(50, 55, 80, 0.3) 100%);
		border-color: rgba(255, 165, 0, 0.25);
		border-left-color: #ffb74d;
		box-shadow:
			0 4px 15px rgba(0, 0, 0, 0.3),
			inset -1px -1px 2px rgba(0, 0, 0, 0.2),
			inset 1px 1px 2px rgba(255, 255, 255, 0.08);
	} */

	:global(html[data-theme='dark']) .disclaimer {
		background: rgba(70, 75, 100, 0.35);
		border-left-color: #ffb74d;
		box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
	}

	:global(html[data-theme='dark']) .disclaimer p {
		color: #a0a0b0;
	}

	:global(html[data-theme='dark']) .disclaimer strong {
		color: #d0d0d0;
	}
</style>
