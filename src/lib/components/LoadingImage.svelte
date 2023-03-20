<script lang="ts">
	import { onMount } from 'svelte';

	export let loadingSrc: string;
	export let src: string;
	export let alt: string = '';
	export let height: string | number | null = null;
	export let width: string | number | null = null;
	export let style: string = '';
	export let sizes: string = '';
	export let srcset: string = '';
	export let decoding: 'auto' | 'sync' | 'async' = 'auto';
	export let imgClass: string = '';

	let isLoading = true;

	onMount(() => {
		const img = new Image();
		img.onload = () => {
			isLoading = false;
		};
		img.src = src;
	});
</script>

{#if isLoading}
	<img
		src={loadingSrc}
		{alt}
		{height}
		{width}
		{style}
		{sizes}
		{srcset}
		{decoding}
		class={imgClass}
		aria-label={alt || 'Image'}
	/>
{:else}
	<img
		{src}
		{alt}
		{height}
		{width}
		{style}
		{sizes}
		{srcset}
		{decoding}
		class={imgClass}
		aria-label={alt || 'Image'}
	/>
{/if}
