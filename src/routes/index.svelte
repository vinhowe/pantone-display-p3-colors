<script context="module" lang="ts">
	export const prerender = true;
</script>

<script lang="ts">

import Chip from "$lib/Chip.svelte";
import colors from "../filtered-p3.json";
import { onMount } from "svelte";

let supportsP3 = true;

onMount(async () => {
	supportsP3 = window.matchMedia("(color-gamut: p3)").matches;
});
</script>

<svelte:head>
	<title>Display P3 exclusive Pantone colors</title>
</svelte:head>

<h1 class="text-3xl mt-8 mb-2">Named Display P3 exclusive Pantone colors</h1>

<p class="mb-12 text-lg">Your display <b>{supportsP3 ? "supports" : "does not support"}</b> the Display P3 color space.
{#if !supportsP3}
<b>Colors will be clipped to sRGB.</b>
{/if}
</p>

<section class="flex flex-wrap gap-y-6 justify-between -mx-2">
	{#each colors.filter(color => color.gamut === "p3") as color}
		<Chip name={color.name} code={color.code} p3={color.p3Short} hex={color.hex} />
	{/each}
</section>