<script>
    let { img, title, text, link } = $props();
</script>

<a class="flex flex-col items-center md:w-2/3 bg-cyan-200/10 rounded-2xl shadow-md backdrop-blur-2xl p-4 gap-2" href={link}>
	<h2 class="text-md xl:text-2xl">{title}</h2>
	<img src={img} alt="" class="w-32 xl:w-64 rounded-2xl object-fill" />
	<p class="text-lg">
		{text}
	</p>
</a>
