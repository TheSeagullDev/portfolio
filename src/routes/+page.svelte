<script>
	import bg from '$lib/assets/bg.jpg';
	import hackpad from '$lib/assets/hackpad.png';
	import football from '$lib/assets/football.png';
	import bingo from '$lib/assets/binary.png';
	import Card from './components/card.svelte';
</script>

<div
	style="background-image: url({bg})"
	class="flex min-h-screen flex-col items-center justify-center gap-8 bg-cover bg-center"
>
	<div
		class="w-1/2 rounded-2xl bg-cyan-950/40 p-4 text-center backdrop-blur-xl transition-all hover:scale-110 md:p-16"
	>
		<h1 class="text-2xl text-cyan-50 md:text-5xl">Hi there! 👋</h1>
		<h2 class="text-lg text-cyan-50 md:text-2xl">
			I'm Noah Siegel, a High Schooler passionate about all things tech.
		</h2>
	</div>
	<div
		class="w-3/4 rounded-2xl bg-cyan-950/40 p-16 text-xl text-cyan-50 backdrop-blur-xl md:text-3xl"
	>
		<h1 class="mb-2 text-3xl">Here's some things I've made...</h1>
		<div class="flex flex-col gap-4 md:flex-row">
			<Card
				img={hackpad}
				title="QLab Macropad"
				text="A macropad I designed and built that can do different macros for QLab, a sound and lighting control software."
				link="https://github.com/TheSeagullDev/theseagulldevs-ultimate-hackpad"
			></Card>
			<Card
				img={football}
				title="College Football Picker"
				text="A full-stack app made in with flask and SQLite to run a family college football tournament. Excel spreadsheets no more!"
				link="https://github.com/TheSeagullDev/college-football-2"
			></Card>
			<Card
				img={bingo}
				title="Binary Bingo Dashboard"
				text="A simple dashboard made in Svelte to run a &quot;Binary Bingo&quot; event to teach middle schoolers the fundamentals of computer science!"
				link="https://github.com/TheSeagullDev/binary-bingo"
			></Card>
		</div>
	</div>
</div>
