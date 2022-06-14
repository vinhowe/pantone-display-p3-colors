<script lang="ts">
	import { buildPng } from './p3';

	export let name: string | undefined;
	export let code: string;
	export let p3: number[];
	export let hex: string;

	const src = buildPng(...p3);
	const workingName = name ?? code;
    const codeId = code.toLowerCase().replaceAll(' ', '-');
</script>

<a href="#{codeId}">
	<div
		class="flex flex-col w-1/2 sm:w-1/3 md:w-36 px-2"
		id={codeId}
	>
		<img {src} alt={workingName} class="w-full mb-1.5" />

		{#if name}
			<p class="text-lg font-medium leading-tight mb-1">{name}</p>
		{/if}

		<p class="text-sm opacity-50 font-mono">{code}</p>

		<p class="text-sm opacity-50 font-mono italic">#{hex}</p>
	</div>
</a>
