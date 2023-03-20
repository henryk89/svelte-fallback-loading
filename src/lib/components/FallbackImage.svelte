<script lang="ts">
	export let fallback: string;
	export let src: string;
	export let alt: string = '';
	export let height: string | number | null = null;
	export let width: string | number | null = null;
	export let style: string = '';
	export let sizes: string = '';
	export let srcset: string = '';
	export let decoding: 'auto' | 'sync' | 'async' = 'auto';
	export let imgClass: string = '';
</script>

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
	{...fallback && { onerror: `this.onerror=null;this.src='${fallback}';` }}
/>
