<script>
	import bg from '$lib/assets/bg.jpg';
	import hackpad from '$lib/assets/hackpad.png';
	import football from '$lib/assets/football.png';
	import bingo from '$lib/assets/binary.png';
	import Card from './components/card.svelte';
	import { GithubIcon, LinkedinIcon } from '@lucide/svelte';
</script>

<div
	class="flex min-h-screen flex-col items-center justify-center gap-8 bg-center p-4"
>
	<div
		class="card rounded-2xl border card-hover border-surface-900-100 preset-filled-primary-500 md:w-1/2 p-4 text-center transition-all hover:scale-105 xl:p-16"
	>
		<h1 class="h1">Hi there! 👋</h1>
		<h2 class="h2">
			I'm Noah Siegel, a high schooler passionate about all things tech.
		</h2>
	</div>
	<div
		class="md:w-3/4 p-4 xl:p-16"
	>
		<h3 class="h3 mb-2 text-xl xl:text-3xl">Here's some things I've made...</h3>
		<div class="flex flex-col gap-4 md:flex-row items-center md:items-stretch">
			<Card
				img={hackpad}
				title="QLab Macropad"
				text="A macropad I designed and built that can do different macros for QLab, a sound and lighting control software."
				link="https://github.com/TheSeagullDev/theseagulldevs-ultimate-hackpad"
			></Card>
			<Card
				img={football}
				title="College Football Picker"
				text="A full-stack app made with Flask and SQLite to run a family college football tournament. Excel spreadsheets no more!"
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
	<div class="card flex divide-x divide-surface-200-800">
		<a href="https://www.linkedin.com/in/noah-siegel-29260737b" class="p-2"><LinkedinIcon /></a>
		<a href="https://github.com/TheSeagullDev" class="p-2"><GithubIcon /></a>
	</div>
</div>
