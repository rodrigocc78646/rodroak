<script>
	import LanguageInfo from "../components/LanguageInfo.svelte";
	import data from "../data/data.js";

	let langs = data
		.reduce((acc, val) => acc.concat(val.langs), [])
		.filter((val, i, self) => self.indexOf(val) === i);
	let sel;
</script>

<style>
	.langs {
		position: fixed;
		bottom: 0;
		left: 0;
		right: 0;
		padding: 7px 10px;
		display: flex;
		justify-content: space-around;
		background-color: var(--clr-background);
		box-shadow: 0 -5px 10px 0 rgba(0, 0, 0, 0.05);
	}

	.langs img {
		height: 35px;
		cursor: pointer;
		transform: scale(1);
		opacity: 0.5;
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
			top: 0;
			bottom: 0;
			left: 15px;
			width: 100px;
			padding: 5px 20px;
			display: flex;
			flex-direction: column;
			justify-content: space-around;
			box-shadow: none;
		}

		.langs img.selected {
			transform: scale(2);
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
				transform: scale(1.8);
			}
		}
	}
</style>

<svelte:head>
	<title>Rodroak - My skills</title>
</svelte:head>

<LanguageInfo
	lang={sel}
	data={data.filter((d) => (sel ? d.langs.includes(sel) : true))} />

<div class="langs">
	{#each langs as lang}
		<img
			on:click={() => {
				if (sel === lang) {
					sel = undefined;
				} else sel = lang;
			}}
			src={`langs/${lang}.svg`}
			alt={`logo of ${lang}`}
			class:none={sel === undefined}
			class:selected={lang === sel} />
	{/each}
</div>
