<script>
	let timelineHeight;
	let windowHeight;
</script>

<style>
	.top {
		position: fixed;
		top: 0;
		right: 0;
		height: 75px;
		width: 140px;
		background-color: var(--clr-background);
		box-shadow: -5px 5px 20px 5px var(--clr-background);
		border-bottom-left-radius: 30px;
	}

	.timeline {
		margin-left: 45px;
		padding: 40px 15px 0 10px;
		max-width: 450px;
		border-left: 1px solid var(--clr-blue);
	}

	img {
		width: 100px;
	}

	.event {
		position: relative;
	}

	.main {
		font-weight: lighter;
		font-size: 1.125rem;
		margin: 35px 0 10px;
	}

	.event:first-of-type .main {
		margin-top: 20px;
		margin-bottom: 15px;
	}

	a {
		font-weight: lighter;
		font-size: 0.75rem;
		color: inherit;
		text-decoration: none;
		display: block;
	}

	.detail {
		margin-left: 20px;
		margin-bottom: 10px;
	}

	.detail h5 {
		font-weight: normal;
		font-size: 0.875rem;
	}

	.detail p {
		font-weight: lighter;
		font-size: 0.875rem;
	}

	.event:last-of-type .detail {
		color: var(--clr-blue);
		opacity: 0.3;
	}

	.timestamp {
		position: absolute;
		top: 0;
		left: 0;
		transform: translate(calc(-100% - 20px), 25%);

		font-weight: lighter;
		font-size: 0.75rem;
		z-index: 5;
	}

	.timestamp::after {
		content: "";
		position: absolute;
		background-color: var(--clr-blue);
		height: 1px;
		width: 10px;
		right: -14.5px;
		top: 50%;
	}

	.event:first-of-type .timestamp {
		color: transparent;
	}

	.event:last-of-type {
		overflow: visible;
		padding-bottom: 100px;
	}

	.event:last-of-type::after {
		content: "";
		position: absolute;
		height: calc(100% - 20px);
		width: 0px;
		border: 2px dashed var(--clr-background);
		left: -12px;
		top: 11px;
	}

	@media (min-width: 750px) {
		img {
			position: absolute;
			top: 0;
			left: 0;
			width: 125px;
			transform: translate(calc(-100% - 20px), 20px);
		}

		.event:first-of-type {
			margin-bottom: 60px;
			margin-top: 30px;
		}
	}

	/* ENTER ANIMATION */

	@keyframes opacity {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}

	@keyframes position {
		from {
			transform: translateY(-30px);
		}
		to {
			transform: translateY(0);
		}
	}

	img,
	.event {
		animation-duration: 300ms;
		animation-timing-function: ease-in-out;
		animation-fill-mode: both;
	}

	img {
		animation-name: opacity;
	}

	.event {
		animation-name: opacity, position;
	}

	.event:nth-of-type(2) {
		animation-delay: 100ms;
	}

	.event:nth-of-type(3) {
		animation-delay: 200ms;
	}

	.event:nth-of-type(4) {
		animation-delay: 300ms;
	}

	.event:nth-of-type(5) {
		animation-delay: 400ms;
	}
</style>

<svelte:window bind:innerHeight={windowHeight} />

<svelte:head>
	<title>about</title>
</svelte:head>

<div class="timeline" bind:clientHeight={timelineHeight}>
	<img src="photo.png" alt="me smiling" />
	<div class="event">
		<span class="timestamp">0</span>
		<p class="main">
			Hello, my name is Rodrigo Carvalho and I am applying for a data journalist
			position at the Economist.
		</p>
		<a href="tel:+351961241823">+351961241823</a>
		<a href="mailto:rodrigocc78646@gmail.com">rodrigocc78646@gmail.com</a>
	</div>
	<div class="event">
		<p class="main">I’ve started with Physics.</p>
		<span class="timestamp">2013</span>
		<div class="detail">
			<h5>IST Lisbon</h5>
			<p>Bachelor in Engineering Physics</p>
		</div>
		<div class="detail">
			<h5>ETH Zürich</h5>
			<h5>École Polytechnique Paris</h5>
			<p>Master in High Energy Physics</p>
		</div>
	</div>
	<div class="event">
		<p class="main">Since then I've been working with data...</p>
		<span class="timestamp">2017</span>
		<div class="detail">
			<h5>Accenture</h5>
			<p>Senior Analyst, AI Team</p>
		</div>
	</div>
	<div class="event">
		<p class="main">
			For the past 2 years I’ve been practising web development.
		</p>
		<span class="timestamp">2018</span>
		<div class="detail">
			<h5>Freelance</h5>
			<p>Web Developer</p>
		</div>
	</div>
	<div class="event final">
		<p class="main">I’m ready to be a data journalist!</p>
		<span class="timestamp">Now</span>
		<div class="detail">
			<h5>The Economist</h5>
			<p>Data Journalist</p>
		</div>
	</div>
</div>
<div class="top" />
