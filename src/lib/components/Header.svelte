<script>
	// @ts-ignore
	import Link from "$lib/components/Link.svelte";
</script>

<header class="safe-area">
	<Link title="EV archive" ref="/" />

	<nav>
		<Link title="About" ref="/about" />
		<Link
			title="@emmavireca"
			ref="https://www.instagram.com/emmavireca"
		/>
	</nav>
</header>

<style>
	header {
		padding-block: var(--size-6);

		display: flex;
		gap: var(--size-8);
		justify-content: space-between;
		align-items: center;
	}

	nav {
		display: flex;
		gap: var(--size-6);
		align-items: center;
	}
</style>