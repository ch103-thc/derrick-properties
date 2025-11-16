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
					Please consult with a qualified professional for personalized advice.
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
		background: linear-gradient(135deg, #1a1a1a 0%, #333 100%);
		color: white;
		padding: 80px 0 60px;
		text-align: center;
	}

	.hero-title {
		font-size: 48px;
		font-weight: 700;
		margin: 0 0 16px 0;
		line-height: 1.2;
	}

	.hero-subtitle {
		font-size: 20px;
		margin: 0;
		opacity: 0.9;
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
		background: white;
		border: 2px solid #e0e0e0;
		border-radius: 0.25rem;
		font-size: 16px;
		font-weight: 600;
		cursor: pointer;
		transition: all 0.3s ease;
		color: #666;
	}

	.toggle-btn:hover {
		border-color: #333;
		background: #f8f8f8;
	}

	.toggle-btn.active {
		background: #1a1a1a;
		color: white;
		border-color: #1a1a1a;
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
		background: white;
		padding: 48px;
		border-radius: 0.25rem;
		box-shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
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
		font-size: 32px;
		font-weight: 700;
		margin: 0 0 12px 0;
	}

	.calculator-description {
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
		border: 2px solid #e0e0e0;
		border-radius: 0.25rem;
		font-size: 16px;
		transition: all 0.3s ease;
	}

	.form-group input[type='number']:focus,
	.form-group input[type='text']:focus {
		outline: none;
		border-color: #333;
	}

	.form-group input[type='range'] {
		width: 100%;
		height: 6px;
		border-radius: 5px;
		background: #e0e0e0;
		outline: none;
		-webkit-appearance: none;
	}

	.form-group input[type='range']::-webkit-slider-thumb {
		-webkit-appearance: none;
		appearance: none;
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background: #1a1a1a;
		cursor: pointer;
	}

	.form-group input[type='range']::-moz-range-thumb {
		width: 20px;
		height: 20px;
		border-radius: 50%;
		background: #1a1a1a;
		cursor: pointer;
		border: none;
	}

	.input-with-display {
		display: flex;
		align-items: center;
		gap: 16px;
	}

	.range-input-box {
		width: 80px !important;
		padding: 8px 12px;
		border: 2px solid #e0e0e0;
		border-radius: 0.25rem;
		font-size: 16px;
		text-align: center;
		transition: all 0.3s ease;
	}

	.range-input-box:focus {
		outline: none;
		border-color: #333;
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
		padding: 12px;
		background: #f0f0f0;
		border: none;
		border-radius: 0.25rem;
		font-weight: 600;
		cursor: pointer;
		transition: all 0.3s ease;
		margin-top: 12px;
		font-family: 'Poppins', sans-serif;
	}

	.reset-btn:hover {
		background: #e0e0e0;
	}

	/* Results Styles */
	.calculator-results {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	.result-card {
		background: #f8f8f8;
		padding: 24px;
		border-radius: 0.25rem;
		border-left: 4px solid #e0e0e0;
	}

	.result-card.primary {
		background: linear-gradient(135deg, #1a1a1a 0%, #333 100%);
		color: white;
		border-left: none;
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

	.breakdown-card {
		background: white;
		border: 2px solid #e0e0e0;
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
	.disclaimer {
		margin-top: 40px;
		padding: 24px;
		background: white;
		border-radius: 0.25rem;
		border-left: 4px solid #ff9800;
		opacity: 0;
		transform: translateY(20px);
		transition: all 0.6s ease;
		transition-delay: 0.3s;
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
</style>
