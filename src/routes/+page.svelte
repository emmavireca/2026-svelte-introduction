<script>
	import Filter from "$lib/components/Filter.svelte";
	import Project from "$lib/components/Project.svelte";
	import Boogie1 from "$lib/assets/Boogie1.jpeg";
	import Boogie2 from "$lib/assets/Boogie2.jpeg";
	import Boogie3 from "$lib/assets/Boogie3.jpeg";
	import Boogieanimazione from "$lib/assets/Boogieanimazione.gif";
	import Zenza from "$lib/assets/zenza.png";
	import Focus from "$lib/assets/focus.png";
	import Basque from "$lib/assets/basque.png";
	import Foto from "$lib/assets/foto.png";
	import Voila from "$lib/assets/Voilà.png";
	import Goccie from "$lib/assets/Goccie.png";
	import Dizionario from "$lib/assets/dizionario.png";
	import Alpha from "$lib/assets/alpha.png";
	import bruco from "$lib/assets/bruco.gif";
	import mockup from "$lib/assets/moc.png";



	const data = {
	years: [
		{
			number: 2026,
			projects: [
				{ data: { title: "Boogie Woogie outdoor", year: "2026", thumbnail:Boogie1 } },
				{ data: { title: "Boogie Woogie central scene", year: "2026", thumbnail: Boogie2 } },
				{ data: { title: "Boogie Woogie final scene", year: "2026", thumbnail: Boogie3 } },
				{ data: { title: "Boogie Woogie animazione", year: "2026", thumbnail: Boogieanimazione } },
				{ data: { title: "Brand Book Zenza Bronica", year: "2026", thumbnail: Zenza } },
				{ data: { title: "Brand Activation", year: "2026", thumbnail: Focus } },
				{ data: { title: "Specimen Baskerville", year: "2026", thumbnail: Basque } },
				{ data: { title: "25 fotografie", year: "2026", thumbnail: Foto } }
			]
		},
		
		{
			number: 2025,
			projects: [
				{ data: { title: "Voilà", year: "2025", thumbnail: Voila } },
				{ data: { title: "Goccie di cristallo", year: "2025", thumbnail: Goccie } },
				{ data: { title: "Dizionario", year: "2025", thumbnail: Dizionario } },
				{ data: { title: "Specimen Alphapipe", year: "2025", thumbnail: Alpha } }
			]
		},
		{
			number: 2024,
			projects: [
				{ data: { title: "Animazione per città invisibili", year: "2024", thumbnail: bruco } },
				{ data: { title: "Mockup per elementi visivi", year: "2024", thumbnail: mockup } }
			]
		}
	]
};

	let currentYear = $state(data?.years?.[0]?.number || 2026);
	let projects = $derived.by(() => {
	if (!data?.years) return [];

	return (
		data.years.find((year) => {
			return year.number == currentYear;
		})?.projects || []
	);
});
</script>

<section class="safe-area hero">
	<h1>
		This archive collects a selection of projects developed over the past years, including both academic work and personal explorations. The navigation below allows you to browse and discover them by year.
	</h1>
</section>

<nav class="safe-area filters">
	{#each data.years as year}
		<Filter bind:group={currentYear} value={year.number} />
	{/each}
</nav>

<section class="safe-area projects">
	{#each projects as project}
		<Project data={project.data} />
	{/each}
</section>

<style>
	.hero {
		padding-block: var(--size-11);

		h1 {
			font-size: var(--size-7);
			max-width: 35ch;

		   @media (max-width: 768px) {
			font-size: var(--size-6);
		   }
		}
	}

	.filters {
		display: flex;
		align-items: center;
		gap: var(--size-5);
	}

	.projects {
		padding-block: var(--size-7);

		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 32px;
		max-width: 1500px;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
		}
	}
</style>