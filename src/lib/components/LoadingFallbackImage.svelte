<script lang="ts">
	import { onMount } from 'svelte';

	export let loadingSrc: string;
	export let fallback: string;
	export let fallbackMs: number = 0;
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

	let image_src = '';

	if (fallbackMs > 0) {
		const timeoutId = setTimeout(() => {
			image_src = fallback;
			isLoading = false;
		}, fallbackMs);
		onMount(() => {
			const img = new Image();
			img.onload = () => {
				if (fallbackMs > 0) {
					clearTimeout(timeoutId);
				}
				isLoading = false;
				image_src = src;
			};
			img.onerror = () => {
				if (fallbackMs > 0) {
					clearTimeout(timeoutId);
				}
				isLoading = false;
				image_src = fallback;
			};
			img.src = src;
		});
	} else {
		onMount(() => {
			const img = new Image();
			img.onload = () => {
				isLoading = false;
				image_src = src;
			};
			img.onerror = () => {
				isLoading = false;
				image_src = fallback;
			};
			img.src = src;
		});
	}
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
		src={image_src}
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
