<script lang="ts">
	import Blorbo from './Blorbo.svelte';
	import PlushRow from './PlushRow.svelte';

	let blorbo: any = $state(undefined);

	function blorbed(index: number) {
		console.log(blorbo);
		blorbo.updateBlorbo(index);
	}
</script>

<div class="w-full">
	<div
		class="relative mr-8 ml-8 h-128 overflow-hidden rounded-b-2xl bg-[#F8F32B] p-8 inset-shadow-lg md:h-164"
	>
		<div class="m-auto flex h-full max-w-250 flex-row align-middle">
			<div class="flex flex-col justify-center">
				<h1 class="poller text-center text-5xl md:text-left md:text-7xl">Shrine</h1>
				<h2 class="text-center font-[Pangolin] text-2xl md:text-left">
					Make and code a project about your favorite fictional character, get a grant to buy merch
					of your character!
				</h2>
				<a
					class="poller mt-8 mr-auto ml-auto w-48 rounded-lg bg-[#2B2D42] p-4 text-center text-lg font-bold text-white underline transition-all hover:w-52 md:mr-0 md:ml-0"
					href="https://snowflake.fillout.com/shrine">RSVP Here!</a
				>
			</div>
			<div class="relative hidden flex-col justify-center md:flex">
				<img src="shrine.png" alt="shrine" class="min-w-96 scale-150" />
				<Blorbo bind:this={blorbo} />
			</div>
		</div>
		<a href="https://hackclub.com/" tabindex="-1">
			<img
				src="https://assets.hackclub.com/flag-orpheus-left.svg"
				class="absolute top-0 left-0 w-48 origin-top-left transition hover:rotate-6"
				alt="hack club flag"
			/>
		</a>
	</div>
</div>

<div class="h-32 my-8 overflow-x-clip">
	<PlushRow {blorbed} />
</div>

<main class="w-full bg-[#2B2D42] p-8 text-white inset-shadow-lg/50">
	<div class="m-auto max-w-250">
		<h1 class="poller mb-4 text-4xl">What is Shrine?</h1>
		<p class="mb-8 font-[Pangolin] text-lg">
			Shrine is a YSWS where you build a project (Must be tracked with Hackatime) about your
			favorite fictional character! It could be anything! Like, a website about your character, a
			Visual Novel with RenPy, anything related to that character! After you submit and we check
			your project, you'll receive a grant to go buy merch of your favorite character!
		</p>
		<h1 class="poller mb-4 text-4xl">How do I join?</h1>
		<p class="mb-8 font-[Pangolin] text-lg">
			Join us at <a
				class="text-[#F8F32B] underline"
				href="https://hackclub.enterprise.slack.com/archives/C09A37XECJV"
			>
				#shrine
			</a>
			and make sure you RSVP on the form above!
		</p>
		<h1 class="poller mb-4 text-4xl">When will this launch?</h1>
		<p class="mb-8 font-[Pangolin] text-lg">
			We dont have an ETA right now since this YSWS draft is freshly new and we haven't found a
			sponsor yet!
		</p>
		<h1 class="poller mb-4 text-4xl">What kind of merch can I buy?</h1>
		<p class="mb-8 font-[Pangolin] text-lg">
			It could be a figurine, hoodies, shirts, stationary, stickers, anything as long it's related
			to your character!
		</p>
		<h1 class="poller mb-4 text-4xl">How many hours do I have to work?</h1>
		<p class="mb-8 font-[Pangolin] text-lg">
			We haven't set how many hours. It might be 5 or 6 hours. Although, this might change, please
			take it with a grain of salt!
		</p>
		<h1 class="poller mb-4 text-4xl">Any policy about AI usage?</h1>
		<p class="mb-8 font-[Pangolin] text-lg">
			Please do not vibe-code your project! You can use AI to get help on your project but please
			dont vibe code it!
		</p>
		<h1 class="poller mb-4 text-4xl">Is there anything I can contribute to this YSWS?</h1>
		<p class="mb-8 font-[Pangolin] text-lg">
			Yes! You can spread the word about this. If you want to co-org this YSWS, free feel to DM one
			of the organizers on Slack (on the bottom of the page) or
			<a class="text-[#F8F32B] underline" href="mailto:me@ifeellikeharukananase.tech">email me</a>!
		</p>
	</div>
</main>

<div class="mt-8 mr-8 ml-8 rounded-t-2xl bg-[#8D99AE] inset-shadow-lg">
	<div
		class="relative m-auto flex max-w-250 flex-col justify-between gap-8 p-8 text-center text-black md:flex-row md:gap-0 md:text-left"
	>
		<div class="flex flex-col">
			<h1 class="poller mb-4 text-3xl font-bold">Links</h1>
			<a href="https://hackclub.com/" class="font-[Pangolin] underline">Hack Club</a>
			<a href="https://auth.hackclub.com/slack" class="font-[Pangolin] underline">Hack Club Slack</a
			>
			<a
				href="https://hackclub.enterprise.slack.com/archives/C09A37XECJV"
				class="font-[Pangolin] underline"
			>
				#shrine Channel
			</a>
		</div>
		<div class="flex flex-col">
			<h1 class="poller mb-4 text-3xl font-bold">Organizers</h1>
			<a
				href="https://app.slack.com/client/E09V59WQY1E/D0A7TQRKCBH"
				class="font-[Pangolin] underline">@Alexander</a
			>
			<a
				href="https://app.slack.com/client/E09V59WQY1E/D079516CS2J"
				class="font-[Pangolin] underline">@Valerie</a
			>
			<a
				href="https://app.slack.com/client/E09V59WQY1E/D0A96GYCKCY"
				class="font-[Pangolin] underline">@Nirvaan</a
			>
		</div>
		<div class="flex flex-col">
			<h1 class="poller mb-4 text-3xl font-bold">Website</h1>
			<a href="https://github.com/Shuflduf/Shrine-Site" class="font-[Pangolin] underline">Github</a>
			<a
				href="https://app.slack.com/client/E09V59WQY1E/D078X2VP0NT"
				class="font-[Pangolin] underline">@Michael</a
			>
		</div>
	</div>
</div>
