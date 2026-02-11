<script>
	let { img, title, text, link } = $props();
</script>

<a
	class="card card-hover preset-filled-surface-100-900 border border-surface-200-800 divide-surface-200-800 divide-y overflow-hidden md:w-2/3"
	href={link}
>
	<header class="h4">
		<img src={img} alt="" class="w-full" />
	</header>
	<main>
		<h4 class="h4 p-4">{title}</h4>
	</main>
	<footer>
		<p class="py-2 px-4">
			{text}
		</p>
	</footer>
</a>
