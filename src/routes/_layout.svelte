<script>
	import Nav from '../components/Nav.svelte';

	export let segment;
</script>

<style>
	main {
		height: 100vh;
	}
</style>

<Nav {segment}/>

<main>
	<slot></slot>
</main>