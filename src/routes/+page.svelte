<script>
	import { onMount } from 'svelte';
	import About from './components/About.svelte';
	import Projects from './components/Projects.svelte';
	import Contact from './components/Contact.svelte';

	const commands = {
		about: About,
		projects: Projects,
		contact: Contact
	};

	const active = false;
	let skipBoot = false;

	function formatDate(date) {
		const days = ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'];
		const months = [
			'Jan',
			'Feb',
			'Mar',
			'Apr',
			'May',
			'Jun',
			'Jul',
			'Aug',
			'Sep',
			'Oct',
			'Nov',
			'Dec'
		];

		return `${days[date.getDay()]} ${months[date.getMonth()]} ${String(date.getDate()).padStart(2, ' ')} ${date.toLocaleTimeString('en-US', { hour12: false })}`;
	}

	let command = $state('');
	let history = $state([]);
	let input = $state();

	function handleKeydown(e) {
		if (e.key === 'Enter') {
			const input = command.trim().toLowerCase();
			const Component = commands[input];

			history.push({
				command: command,
				component: Component
			});

			command = '';
		}
	}

	function focusInput() {
		input?.focus();
	}
	let lines = $state([]);

	const sleep = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

	const getRandomTime = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;

	async function startLoadingLoop(message, unit) {
		const id = Math.random().toString(36).slice(2, 7);

		const size = Math.floor(Math.random() * 901) + 100;
		const count = Math.floor(Math.random() * 10) + 1;

		for (let i = 1; i <= count; i++) {
			const progress = Math.round((i / count) * size);

			lines.push(`${message} ${progress}/${size}${unit}`);

			if (i < count) {
				const delay = getRandomTime(50, 200);

				await sleep(delay);
			}
		}

		clear();
	}

	function clear() {
		lines = [];
	}

	const loadingReasons = active
		? [
				'Loading portfolio',
				'Indexing projects',
				'Parsing metadata',
				'Resolving dependencies',
				'Building project tree',
				'Initializing components',
				'Mounting workspace'
			]
		: ['Loading portfolio', 'Checking workspace', 'Mounting terminal'];

	let booted = $state(false);
	async function boot() {
		for (const reason of loadingReasons) {
			await startLoadingLoop(reason, '');
		}
		booted = true;
		focusInput();
	}

	if (!skipBoot) {
		boot();
	} else {
		booted = true;
	}
</script>

<div
	class="relative min-h-screen overflow-hidden bg-black font-vt323 text-white"
	role="textbox"
	aria-multiline="true"
	aria-label="Terminal"
	tabindex="-1"
	onclick={focusInput}
	onkeydown={(e) => {
		if (e.key === 'Tab') {
			focusInput();
		}
	}}
>
	<div class="p-4 text-xl">
		{#each lines as line}
			<p class="-my-2">{line}</p>
		{/each}
		{#if booted}
			<p>Last login: {formatDate(new Date())} on ttys000</p>
			{#if active}
				<p>noahsiegel@portfolio ~ % whoami</p>
				<p class="text-blue-400">
					Hello there! I'm Noah Siegel, a CS student studying at <span class="text-yellow-500"
						>Georgia Tech</span
					>.
				</p>
				<p class="text-blue-400">
					Most of my projects are built in SvelteKit, but I'm also interested in hardware, PCB
					design, and learning about new frameworks and technologies.
				</p>
				<p class="text-blue-400">
					To learn more about who I am, type <span class="text-red-400">about</span>
				</p>
				<p class="text-blue-400">
					To learn more about what I've made, type <span class="text-green-400">projects</span>
				</p>
				<p class="text-blue-400">
					To learn more about how to contact me, type <span class="text-purple-400">contact</span>
				</p>
				<p class="text-blue-200">Thanks for visiting!</p>
				{#each history as item}
					<p>noahsiegel@portfolio ~ % {item.command}</p>

					{#if item.component}
						<item.component />
					{:else}
						<p>command not found: {item.command}</p>
					{/if}
				{/each}
				<p>
					noahsiegel@portfolio ~ % {command}<span class="blink text-sm">█</span>
				</p>
			{:else}
				<p>noahsiegel@portfolio ~ % cat status</p>
				<p class="text-yellow-500">coming soon</p>
				<p class="text-blue-400">Check back later for the full portfolio.</p>
				<p>
					<a class="text-blue-200" href="https://linkedin.com/in/noahjsiegel2">LinkedIn</a> |
					<a class="text-blue-200" href="https://github.com/theseagulldev">GitHub</a>
					| <a class="text-blue-200" href="/resume.pdf">Resume</a> | 
					<a class="text-blue-200" href="mailto:noah@noahsiegel.dev">Contact</a>
				</p>
				<p>noahsiegel@portfolio ~ % <span class="blink text-sm">█</span></p>
			{/if}
		{/if}
		{#if active}
			<input
				bind:this={input}
				bind:value={command}
				onkeydown={handleKeydown}
				class="pointer-events-none absolute opacity-0"
				autofocus
			/>
		{/if}
	</div>
	<div
		class="pointer-events-none absolute inset-0 bg-[linear-gradient(to_bottom,transparent_50%,rgba(0,0,0,0.15)_50%)] bg-[length:100%_4px]"
	></div>
</div>

<style>
	@keyframes blink {
		50% {
			opacity: 0;
		}
	}

	.blink {
		animation: blink 1s step-end infinite;
	}
</style>
