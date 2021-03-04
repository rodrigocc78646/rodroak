<script>
	import LanguageInfo from "../components/LanguageInfo.svelte";
	import data from "../data/data.js";

	let langs = ["python", "react", "svelte", "d3", "aws"];
	let sel;

	let scrollY;
</script>

<style>
	.langs {
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		padding: 7px 10px;
		background-color: var(--clr-background);
		box-shadow: 0 -5px 10px 0 rgba(0, 0, 0, 0.05);
	}

	.langs > div {
		width: 100%;
		display: flex;
		justify-content: space-around;
	}

	.langs img {
		height: 30px;
		max-width: 40px;
		cursor: pointer;
		transform: scale(1);
		opacity: 0.3;
		transition: all 100ms ease-in-out;
	}

	.langs img.selected {
		opacity: 1;
		transform: scale(1.2);
	}

	.langs img.none {
		transform: scale(1);
		opacity: 1;
	}

	@media (hover: hover) {
		.langs img:hover {
			transform: scale(1.05);
		}

		.langs img.selected:hover {
			transform: scale(1.05);
		}
	}

	@media (min-width: 600px) {
		.langs {
			position: fixed;
			left: 15px;
			top: 0;
			bottom: 0;
			width: 100px;
			padding: 5px 20px;
			display: flex;
			flex-direction: column;
			justify-content: center;
			box-shadow: none;
		}

		.langs > div {
			height: 600px;
			max-height: 100%;
			display: flex;
			flex-direction: column;
			justify-content: space-around;
		}

		.langs img {
			height: 35px;
			max-width: 45px;
		}

		.langs img.selected {
			transform: scale(1.5);
			opacity: 1;
		}

		.langs img.none {
			transform: scale(1);
			opacity: 1;
		}

		@media (hover: hover) {
			.langs img:hover {
				transform: scale(1.2);
			}

			.langs img.selected:hover {
				transform: scale(1.4);
			}
		}
	}

	/* ANIMATION */

	@keyframes enter-bottom {
		from {
			opacity: 0;
			transform: scaleY(0);
		}
		80% {
			opacity: 1;
			transform: scaleY(1.1);
		}
		to {
			opacity: 1;
			transform: scaleY(1);
		}
	}

	@keyframes enter-side {
		from {
			opacity: 0;
			transform: translateX(-200%);
		}
		80% {
			opacity: 1;
			transform: translateX(10%);
		}
		to {
			opacity: 1;
			transform: translateX(0);
		}
	}

	.langs {
		animation-name: enter-bottom;
		animation-duration: 500ms;
		animation-delay: 500ms;
		animation-timing-function: ease-in-out;
		animation-fill-mode: both;
		transform-origin: bottom;
	}

	@media (min-width: 600px) {
		.langs {
			animation-name: enter-side;
			transform-origin: left;
		}
	}
</style>

<svelte:head>
	<title>my skills</title>
</svelte:head>

<svelte:window bind:scrollY />

<LanguageInfo
	lang={sel}
	data={data.filter((d) => (sel ? d.langs.includes(sel) : true))} />

<div class="langs">
	<div>
		{#each langs as lang}
			<img
				on:click={() => {
					if (sel === lang) {
						sel = undefined;
					} else sel = lang;
					scrollY = 0;
				}}
				src={`langs/${lang}.svg`}
				alt={`logo of ${lang}`}
				class:none={sel === undefined}
				class:selected={lang === sel} />
		{/each}
	</div>
</div>
