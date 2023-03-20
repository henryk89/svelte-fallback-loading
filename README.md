# svelte-fallback-loading

A svelte component library to handle slow and non existent images.

## Installation

`npm i svelte-time`

## Components

`FallbackImage` Configure a fallback image src that will be used if the primary image cannot be loaded.

```
<FallbackImage src="primary_image.png" fallback="fallback_image.png" />
```

<br>

`LoadingImage` Configure an image src that will be displayed while the primary image loads.

```
<LoadingImage loadingSrc="loading_image.png" src="primary_image.png" />
```

<br>

`LoadingFallbackImage` A mix of the previous 2 components, this allows you to configure a loading image and a fallback image. A fallback time can be configured as well, this will display the fallback if the primary image cannot be loaded within a timeframe.

```
<LoadingFallbackImage loadingSrc="loading_image.png" src="primary_image.png" fallback="fallback_image.png" />
```

or

```
<LoadingFallbackImage fallbackMs={2000} loadingSrc="loading_image.png" src="primary_image.png" fallback="fallback_image.png" />
```

## Props

| Name       | Type                       | Note                                               |
| ---------- | -------------------------- | -------------------------------------------------- |
| src        | string                     |                                                    |
| fallback   | string                     | Only on `FallbackImage` and `LoadingFallbackImage` |
| loadingSrc | string                     | Only on `LoadingImage` and `LoadingFallbackImage`  |
| fallbackMs | number                     | Only on `LoadingFallbackImage`                     |
| alt        | string                     |                                                    |
| height     | string or number           |                                                    |
| width      | string or number           |                                                    |
| sizes      | string                     |                                                    |
| srcset     | string                     |                                                    |
| decoding   | "auto" or "sync" or "async | Set to "auto" by default                           |
| imgClass   | string                     | Img class attribute                                |
