<script lang="ts">
	import { onMount } from 'svelte';

	const PLUSHIE_SIZE: number = 128;
	const PLUSHIES = [
		'acrid.png',
		'astrobot.png',
		'banjo.png',
		'claire.png',
		'ena.png',
		'gup.png',
		'kita.png',
		'knight.png',
		'madotsuki.png',
		'niko.png',
		'peppino.png',
		'quaber.png',
		'riebek.png',
		'sans.png',
		'shovelknight.png',
		'skelly.png',
		'slime.png',
		'spamtong.png'
	];
	let plushieBag: number[] = [];
	let activePlushies: number[] = $state([]);
	let position: number = $state(0.0);

	onMount(() => {
		requestAnimationFrame(update);
	});

	function update(currentTime: number) {
		position = currentTime / 10.0;

		// const firstPlushPos = position;
		// if (activePlushies.length > 0 && firstPlushPos > window.innerWidth + PLUSHIE_SIZE) {
		// 	activePlushies.shift();
		// }

		const lastPlushPos = position - (activePlushies.length - 1) * PLUSHIE_SIZE;
		if (lastPlushPos > PLUSHIE_SIZE) {
			activePlushies.push(nextPlushie());
		}

		requestAnimationFrame(update);
	}

	function nextPlushie(): number {
		if (plushieBag.length <= 0) {
			// activePlushieCooldown += delta;
			// if (activePlushieCooldown > PLUSHIE_COOLDOWN) {
			// 	console.log('FUCK');
			// 	activePlushies.push(nextPlushie());
			// 	activePlushieCooldown = 0.0;
			// }

			plushieBag = Array.from({ length: PLUSHIES.length }, (_, i) => i);
			shuffle(plushieBag);
			console.log(plushieBag);
		}
		return plushieBag.pop() as number;
	}

	function shuffle(array: any[]) {
		for (let i = array.length - 1; i > 0; i--) {
			const j = Math.floor(Math.random() * (i + 1));
			[array[i], array[j]] = [array[j], array[i]];
		}
		return array;
	}
</script>

<div class="relative flex flex-row">
	{#each activePlushies as plushI, i}
		{#if position - i * PLUSHIE_SIZE < window.innerWidth}
			<img
				src={`plushies/${PLUSHIES[plushI]}`}
				style={`left: ${position - (i + 1) * PLUSHIE_SIZE}px; width: ${PLUSHIE_SIZE}px`}
				class="absolute"
				alt={PLUSHIES[plushI]}
			/>
		{/if}
	{/each}
</div>
