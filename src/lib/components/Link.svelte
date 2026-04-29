<script>
	import Icon from "$lib/components/Icon.svelte";

	const {
		ref,
		title = null,
		children = null,
		leadingIcon = null,
		trailingIcon = null,
	} = $props();
</script>

<a href={ref}>
	{#if children}
		{@render children()}
	{:else}
		{#if leadingIcon}
			<Icon name={leadingIcon} />
		{/if}

		{title}

		{#if trailingIcon}
			<Icon name={trailingIcon} />
		{/if}
	{/if}
</a>

<style>
	a {
		display: inline-flex;
		align-items: center;
		gap: var(--size-1);
		color: var (--color-link--default);

		transition: color 0.75s var(--ease-out-quart);

		&:hover {
			color: var(--color-link--hover);
		}
	}
</style>