<script lang="ts">
	import dice from '$lib/assets/icon-dice.svg';
	import dividerDesk from '$lib/assets/pattern-divider-desktop.svg';
	import dividerMob from '$lib/assets/pattern-divider-mobile.svg';

	let advice: string = '';
	let id: number = 0;
	const getQuotes = async () => {
		const quotes = await fetch("https://api.adviceslip.com/advice", {
      cache: "no-cache",
    })
		const data = await quotes.json();
		advice = data.slip.advice;
		id = data.slip.id;
	}
	getQuotes();
</script>

<div class="bg-blue-2 rounded-xl p-8 relative text-center flex flex-col items-center w-5/6 max-w-lg">
	<h1 class="text-neon uppercase tracking-widest text-[1rem] mb-6">advice #{id}</h1>
	<p class="text-cyan md:text-2xl text-[1.2rem] font-extrabold">"{advice}"</p>
	<img class="hidden md:block my-6" src="{dividerDesk}" alt="logo">
	<img class="my-6 md:hidden" src="{dividerMob}" alt="logo">
	<button
		on:click="{getQuotes}"
		class="absolute -bottom-6 bg-neon shadow hover:shadow-neon transition-all hover:shadow-[0px_0px_40px_1px] rounded-full p-3 text-2xl text-white"
	>
		<img class="w-5" src="{dice}" alt="">
	</button>
</div>
