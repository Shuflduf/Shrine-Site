<script lang="ts">
	import { PLUSHIES } from '$lib';
	import { onMount } from 'svelte';

	let { blorbed }: { blorbed: (arg0: number) => void } = $props();

	const PLUSHIE_SIZE: number = 128;
	let plushieBag: number[] = [];
	type PlushieRowItem = {
		id: string;
		plushIndex: number;
	};
	let activePlushies: PlushieRowItem[] = $state([]);
	let removedPlushies: number = $state(0);
	let position: number = $state(0.0);
	let currentPlushieIndex: number = 0;

	onMount(() => {
		plushieBag = Array.from({ length: PLUSHIES.length }, (_, i) => i);
		shuffle(plushieBag);
		requestAnimationFrame(update);
	});

	function update(currentTime: number) {
		position = currentTime / 10.0;

		const firstPlushPos = position - (removedPlushies + 1) * PLUSHIE_SIZE;

		if (activePlushies.length > 0 && firstPlushPos > window.innerWidth + PLUSHIE_SIZE) {
			activePlushies.shift();
			removedPlushies += 1;
		}

		const lastPlushPos = position - (activePlushies.length + removedPlushies - 1) * PLUSHIE_SIZE;
		if (lastPlushPos > PLUSHIE_SIZE) {
			activePlushies.push({ id: crypto.randomUUID(), plushIndex: plushieBag[currentPlushieIndex] });
			currentPlushieIndex += 1;
			currentPlushieIndex %= PLUSHIES.length;
		}

		requestAnimationFrame(update);
	}

	function shuffle(array: any[]) {
		for (let i = array.length - 1; i > 0; i--) {
			const j = Math.floor(Math.random() * (i + 1));
			[array[i], array[j]] = [array[j], array[i]];
		}
		return array;
	}
</script>

<div class="relative flex h-full flex-row">
	{#each activePlushies as item, i (item.id)}
		<button
			tabindex="-1"
			onclick={() => blorbed(item.plushIndex)}
			style={`left: ${position - (i + removedPlushies + 1) * PLUSHIE_SIZE}px; width: ${PLUSHIE_SIZE}px`}
			class="absolute cursor-pointer overflow-visible transition hover:scale-110"
		>
			<img
				src={`plushies/${PLUSHIES[item.plushIndex]}`}
				alt={PLUSHIES[item.plushIndex]}
				style={`width: ${PLUSHIE_SIZE}px;`}
			/>
		</button>
	{/each}
</div>
