<script>
	export let videoId;
	export let width = '560';
	export let height = '315';
</script>

<div class="w-full max-w-xl mx-auto my-8">
	<div class="relative h-0" style="padding-bottom: 56.25%">
		<iframe
			title="YouTube video player"
			class="absolute top-0 left-0 w-full h-full"
			src={`https://www.youtube.com/embed/${videoId}`}
			{width}
			{height}
			frameborder="0"
			allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
			allowfullscreen />
	</div>
</div>
