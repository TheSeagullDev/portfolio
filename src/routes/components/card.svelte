<script>
    let { img, title, text, link } = $props();
</script>

<a class="flex flex-col items-center w-2/3 bg-cyan-200/10 rounded-2xl shadow-md backdrop-blur-2xl p-4 gap-2" href={link}>
	<h2 class="text-2xl">{title}</h2>
	<img src={img} width="256px" alt="" class="rounded-2xl object-fill" />
	<p class="text-lg">
		{text}
	</p>
</a>
