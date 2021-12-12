<script lang="ts">
	import Header from './components/Header.svelte';
  	import Section from './components/Section.svelte';
	import Tipjar from './components/Tipjar.svelte';

	interface SectionData {
		title: string;
		src: string;
	};

	const sections: SectionData[] = [
		{
			src: 'image1.jpg',
			title: 'Light piece #231'
		},
		{
			src: 'image2.jpg',
			title: 'Light piece #039'
		},
		{
			src: 'image3.jpg',
			title: 'Light piece #039a'
		},
		{
			src: 'image4.jpg',
			title: 'Light piece #13'
		}
	];
</script>

<main>
	<Header/>
	{#each sections as section}
		<Section src={section.src} title={section.title} />
	{/each}
	<Tipjar/>
</main>

<style></style>