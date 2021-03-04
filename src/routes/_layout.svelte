<script>
	import Nav from "../components/Nav.svelte";

	export let segment;
</script>

<style>
	main {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		min-height: 100vh;
	}
</style>

<Nav {segment} />

<main>
	<slot />
</main>
