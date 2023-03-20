<script>
	import FallbackImage from "$lib/components/FallbackImage.svelte";
	import LoadingFallbackImage from "$lib/components/LoadingFallbackImage.svelte";
	import LoadingImage from "$lib/components/LoadingImage.svelte";
</script>

<FallbackImage src="primary_image.png" fallback="fallback_image.png" />

<LoadingImage loadingSrc="loading_image.png" src="primary_image.png" />

<LoadingFallbackImage fallbackMs={2000} loadingSrc="loading_image.png" src="primary_image.png" fallback="fallback_image.png" />