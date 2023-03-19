<script>
	import FaTwitter from 'svelte-icons/fa/FaTwitter.svelte';
	import FaLinkedinIn from 'svelte-icons/fa/FaLinkedinIn.svelte';
	import FaYoutube from 'svelte-icons/fa/FaYoutube.svelte';

	// NOTE(julieta) we can change this to AMSDS or smtn
	let datasetName = 'Pit30M';

	export let samples = [
		{ src: 'sample_image_1.jpg', alt: 'Urban Scene - Daytime' },
		{ src: 'sample_image_2.jpg', alt: 'Highway - Nighttime' },
		{ src: 'sample_image_3.jpg', alt: 'Lidar Scan - Intersection' }
		// ...more samples
	];
</script>

<header class="bg-white shadow-sm py-4">
	<div class="container mx-auto px-4 flex justify-between items-center">
		<div class="text-xl font-semibold">
			{datasetName}
		</div>
		<nav>
			<ul class="flex space-x-6">
				<li><a href="#" class="text-gray-600 hover:text-gray-900">Home</a></li>
				<li>
					<a href="https://github.com/user/repo" class="text-gray-600 hover:text-gray-900">GitHub</a>
				</li>
				<li>
					<a href="https://youtu.be/video-url" class="text-gray-600 hover:text-gray-900">Video</a>
				</li>
				<li>
					<a href="https://arxiv.org/abs/paper-url" class="text-gray-600 hover:text-gray-900">Paper</a>
				</li>
				<li>
					<a href="https://dataset-url" class="text-white bg-blue-600 hover:bg-blue-700 px-4 py-2 rounded"
						>Download Dataset</a>
				</li>
			</ul>
		</nav>
	</div>
</header>

<!-- Background image 1 from https://unsplash.com/photos/F6Kj8ovnUvM -->
<!-- Background image 2 from https://unsplash.com/photos/yLcPSvJkGrM -->
<section class="bg-cover bg-center h-96 relative" style="background-image: url('hero_bg.jpg')">
	<div class="container mx-auto px-4 h-full flex items-center backdrop-blur-sm bg-black/30">
		<div class="text-white">
			<h1 class="text-4xl font-bold">
				{datasetName}: The Benchmark for Global Localization in the Age of Self-Driving Cars
			</h1>
			<p class="text-xl mt-4">Explore the future of autonomous vehicle localization with our comprehensive dataset.</p>
			<a href="https://dataset-url" class="bg-blue-600 hover:bg-blue-700 text-white mt-6 px-6 py-3 rounded inline-block"
				>Get Started</a>
		</div>
	</div>
</section>

<section class="container mx-auto px-4 py-12">
	<h2 class="text-3xl font-bold mb-8">Introducing {datasetName}</h2>
	<p class="text-lg mb-8">Brief description of the dataset, its purpose, and key features.</p>
	<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
		<!-- Add more metrics if needed -->
		<div class="border p-4 rounded">
			<h3 class="font-bold mb-4">Partitions</h3>
			<p>Value or description of the dataset partitions</p>
		</div>
		<div class="border p-4 rounded">
			<h3 class="font-bold mb-4">Number of Images</h3>
			<p>Value or description of the number of images</p>
		</div>
		<div class="border p-4 rounded">
			<h3 class="font-bold mb-4">Sensors</h3>
			<p>Value or description of the sensors used</p>
		</div>
		<div class="border p-4 rounded">
			<h3 class="font-bold mb-4">Location</h3>
			<p>Value or description of the dataset location</p>
		</div>
		<div class="border p-4 rounded">
			<h3 class="font-bold mb-4">Metadata</h3>
			<p>Value or description of the metadata included</p>
		</div>
	</div>
</section>

<section class="container mx-auto px-4 py-12">
	<h2 class="text-3xl font-bold mb-8">Sample Data</h2>
	<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
		{#each samples as { src, alt }}
			<div>
				<img {src} {alt} class="w-full rounded shadow" />
				<p class="mt-4">{alt}</p>
			</div>
		{/each}
	</div>
</section>

<section class="container mx-auto px-4 py-12">
	<h2 class="text-3xl font-bold mb-8">Why Choose {datasetName}?</h2>
	<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
		<!-- Add more features if needed -->
		<div>
			<div class="text-5xl mb-4">🔍</div>
			<h3 class="font-bold mb-4">High-Quality Data</h3>
			<p>
				Our dataset has been meticulously curated to ensure accurate, reliable, and diverse data for benchmarking
				localization algorithms.
			</p>
		</div>
		<div>
			<div class="text-5xl mb-4">📄</div>
			<h3 class="font-bold mb-4">Comprehensive Metadata</h3>
			<p>
				Pit30m includes detailed metadata for each data point, providing valuable context and facilitating in-depth
				analysis.
			</p>
		</div>
		<div>
			<div class="text-5xl mb-4">🔓</div>
			<h3 class="font-bold mb-4">Open-Source</h3>
			<p>
				Pit30m is freely available for academic and research purposes, promoting collaboration and innovation in the
				self-driving car community.
			</p>
		</div>
	</div>
</section>

<footer class="bg-gray-200 py-8">
	<div class="container mx-auto px-4">
		<div class="flex justify-between items-center">
			<div class="text-gray-600">
				<a href="https://github.com/user/repo" class="mr-4 hover:text-gray-900">GitHub</a>
				<a href="https://youtu.be/video-url" class="mr-4 hover:text-gray-900">Video</a>
				<a href="https://arxiv.org/abs/paper-url" class="hover:text-gray-900">Paper</a>
			</div>
			<div class="text-gray-600">
				<p>
					Email:
					<a href="mailto:info@pit30m.com" class="hover:text-gray-900">info@pit30m.com</a>
				</p>
				<div class="flex space-x-4 mt-4">
					<a href="https://twitter.com/pit30m" class="text-gray-600 hover:text-gray-900">
						<div class="icon text-gray-600">
							<FaTwitter />
						</div>
					</a>
					<a href="https://linkedin.com/company/pit30m" class="text-gray-600 hover:text-gray-900">
						<div class="icon text-gray-600">
							<FaLinkedinIn />
						</div>
					</a>
					<a href="https://youtube.com/channel/pit30m" class="text-gray-600 hover:text-gray-900">
						<div class="icon text-gray-600">
							<FaYoutube />
						</div>
					</a>
				</div>
			</div>
			<div class="mt-8 text-center text-gray-600">
				<p>&copy; 2023 {datasetName}. All rights reserved.</p>
			</div>
		</div>
	</div>
</footer>

<style>
	.icon {
		width: 32px;
		height: 32px;
	}
</style>
