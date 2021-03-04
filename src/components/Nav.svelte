<script>
	export let segment;
</script>

<style>
	nav {
		position: fixed;
		display: flex;
		flex-direction: column;
		align-items: flex-end;
		right: 20px;
		top: 0.5rem;
		z-index: 5;
	}

	h1,
	a {
		font-weight: var(--fw-light);
	}

	h1 {
		font-size: 2.125rem;
		letter-spacing: -0.5px;
	}

	.nav {
		display: flex;
	}

	a {
		text-decoration: none;
		font-size: 0.875rem;
		letter-spacing: -0.2px;
		margin-left: 5px;
		color: inherit;
		opacity: 0.3;
	}

	a:focus,
	a:hover {
		opacity: 0.5;
	}

	a.current,
	a.current:hover,
	a.current:focus {
		opacity: 1;
	}
</style>

<nav>
	<h1>rodroak</h1>
	<div class="nav">
		<a href="/" class:current={segment === undefined}>my skills</a>
		<a href="/about" class:current={segment === 'about'}>about</a>
	</div>
</nav>
