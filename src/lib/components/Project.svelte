<script>
	import Icon from "./Icon.svelte";

	const { data: project } = $props();
</script>

{#if project.link}
	<a href={project.link} target="_blank">
		{@render card(project)}
	</a>
{:else}
	{@render card(project)}
{/if}

{#snippet card(project)}
	<article>
		<div class="thumbnail">
				<div class="veil"></div>
			<img src={project.thumbnail} alt={project.title} />
		</div>

		<header>
			<hgroup>
				<h3>{project.title}</h3>
				<span>/ {project.year}</span>
			</hgroup>

				<div class="arrow">
					<Icon name="arrow-up-right" />
				</div>
		</header>
	</article>
{/snippet}

<style>
	article {
		width: 100%;
		display: flex;
		flex-direction: column;
		gap: 8px;
		--veil-opacity: 0;

		&:hover {
			--veil-opacity: 0.1;

			.arrow {
				transform: translateY(0);
			}
		}
	}

	.veil {
			position: absolute;
			width: 100%;
			height: 100%;
			background-color: var(--hex-brand-300);
			mix-blend-mode: multiply;

			transition: opacity 0.4s ease;
			opacity: var(--veil-opacity);
		}

	.thumbnail {
		position: relative;
		aspect-ratio: 4/3;
		overflow: hidden;
		border-radius: 20px;

		img {
			width: 100%;
			height: 100%;
			object-fit: cover;
			display:block;
		}
	}

	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: var(--size-4);
        overflow: hidden
	}

	hgroup {
		display: flex;
		align-items: center;
		gap: var(--size-2);

		span {
			color: var(--color-ink-secondary);
		}
	}

	.arrow {
		transition: transform 0.75s var(--ease-out-quart);
		transform: translateY(100%);
	}

	:global(article:hover .veil) {
    opacity: 1 !important;
}
</style>