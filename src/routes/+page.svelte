<script lang="ts">
	import dice from '$lib/assets/icon-dice.svg';
	import dividerDesk from '$lib/assets/pattern-divider-desktop.svg';
	import dividerMob from '$lib/assets/pattern-divider-mobile.svg';

	let advice: string = '';
	let id: number = 0;
	const getQuotes = async () => {
		const quotes = await fetch('https://api.adviceslip.com/advice');
		const data = await quotes.json();
		advice = data.slip.advice;
		id = data.slip.id;
	}
	getQuotes();
</script>

<div class="bg-blue-2 rounded-xl p-8 relative text-center flex flex-col items-center w-5/6 max-w-lg">
	<h1 class="text-neon uppercase tracking-widest text-xs mb-6">advice #{id}</h1>
	<p class="text-cyan text-2xl font-extrabold">"{advice}"</p>
	<img class="hidden md:block my-6" src="{dividerDesk}" alt="">
	<img class="my-6 md:hidden" src="{dividerMob}" alt="">
	<button
		on:click="{getQuotes}"
		class="absolute -bottom-6 bg-neon shadow rounded-full p-3 text-2xl text-white"
	>
		<img class="w-5" src="{dice}" alt="">
	</button>
</div>
