<script lang="ts">
	import FaTwitter from 'svelte-icons/fa/FaTwitter.svelte';
	import FaLinkedinIn from 'svelte-icons/fa/FaLinkedinIn.svelte';
	import FaYoutube from 'svelte-icons/fa/FaYoutube.svelte';
	import FaFilePdf from 'svelte-icons/fa/FaFilePdf.svelte';
	import FaGithub from 'svelte-icons/fa/FaGithub.svelte';

	import PointCloudViewer from '../PointCloudViewer.svelte';
	import YouTube from 'svelte-youtube-embed';

	// NOTE(julieta) we can change this to AMSDS or smtn
	// let datasetName = 'Pit30M';
	let datasetName = 'Aurora Multi-Sensor Dataset';

	// export let samples = [
	// 	{ src: 'sample_image_1.jpg', alt: 'Urban Scene - Daytime' },
	// 	{ src: 'sample_image_2.jpg', alt: 'Highway - Nighttime' },
	// 	{ src: 'sample_image_3.jpg', alt: 'Lidar Scan - Intersection' }
	// 	// ...more samples
	// ];
</script>

<svelte:head>
	<title>Aurora Multi-Sensor Dataset</title>
</svelte:head>

<header class="bg-white shadow-sm py-4">
	<div class="container mx-auto px-4 flex justify-between items-center">
		<div class="text-xl font-semibold">{datasetName}</div>
		<nav>
			<ul class="flex space-x-6">
				<li><a href="#" class="text-gray-600 hover:text-gray-900">Home</a></li>
				<li>
					<a href="https://github.com/pit30m/pit30m" class="text-gray-600 hover:text-gray-900">DevKit</a>
				</li>
				<li>
					<a href="https://youtu.be/hJ6A_1YSITo" class="text-gray-600 hover:text-gray-900">Video</a>
				</li>
				<li>
					<a href="https://arxiv.org/abs/2012.12437" class="text-gray-600 hover:text-gray-900">Paper</a>
				</li>
				<li>
					<a href="https://github.com/pit30m/pit30m" class="text-white bg-blue-600 hover:bg-blue-700 px-4 py-2 rounded"
						>Download Dataset</a>
				</li>
			</ul>
		</nav>
	</div>
</header>

<!-- Background image 1 from https://unsplash.com/photos/F6Kj8ovnUvM -->
<!-- Background image 2 from https://unsplash.com/photos/yLcPSvJkGrM -->
<!-- <section class="bg-cover bg-center h-96 relative" style="background-image: url('hero_bg.jpg')"> -->
<section class="h-96 relative">
	<div class="container mx-auto px-4 h-full flex items-center backdrop-blur-xl">
		<div class="text-black text-center w-full">
			<h1 class="text-4xl font-bold">
				{datasetName}: The Largest Self-Driving Dataset Released to Date
			</h1>
			<p class="text-2xl mt-4">
				<a class="text-blue-600 hover:underline" href="https://una-dinosauria.github.io/">Julieta Martinez</a><sup>1</sup>
				<a class="text-blue-600 hover:underline" href="https://www.cs.toronto.edu/~doubovs/">Sasha Doubov</a><sup>1,2</sup>, 
				Jack Fan<sup>1</sup>, 
				<a class="text-blue-600 hover:underline" href="https://siegedog.com/">Ioan Andrei Bârsan</a><sup>1,3</sup>, 
				<a class="text-blue-600 hover:underline" href="https://shenlong.web.illinois.edu/">Shenlong Wang</a><sup>1,3</sup>, 
				Gellért Máttyus<sup>1</sup>, 
				<a class="text-blue-600 hover:underline" href="http://www.cs.toronto.edu/~urtasun/">Raquel Urtasun</a><sup>1,3</sup>
			</p>
			<p class="text-2xl mt-4">
				<sup>1</sup> Uber Advanced Technologies Group,
				<sup>2</sup>University of Waterloo,
				<sup>3</sup>University of Toronto
			</p>
			<a
				href="https://arxiv.org/abs/2012.12437"
				class="bg-blue-600 hover:bg-blue-700 text-white mt-6 px-6 py-3 rounded-l-lg inline-block text-2xl">
				<span class="icon">
					<FaFilePdf />
				</span> Paper
			</a>
			<a
				href="https://youtu.be/hJ6A_1YSITo"
				class="bg-blue-600 hover:bg-blue-700 text-white mt-6 px-6 py-3 inline-block text-2xl">
				<span class="icon">
					<FaYoutube />
				</span> Video
			</a>
			<a
				href="https://github.com/pit30m/pit30m"
				class="bg-blue-600 hover:bg-blue-700 text-white mt-6 px-6 py-3 rounded-r-lg inline-block text-2xl">
				<span class="icon">
					<FaGithub />
				</span> DevKit
			</a>
		</div>
	</div>
</section>

<section class="container mx-auto px-4 py-4">
	<div class="grid">
		<h2 class="text-3xl font-bold mb-8">Video</h2>
		<!-- <p class="text-xl"></p> -->
		<!-- <br /> -->
		<div>
			<YouTube id="hJ6A_1YSITo" />
		</div>
	</div>
</section>

<section class="container mx-auto px-4 py-4">
	<div class="grid">
		<h2 class="text-3xl font-bold mb-8">Abstract</h2>
		<div><p class="text-xl">
			We are interested in understanding whether retrieval-based localization approaches are good enough in the context of self-driving vehicles. Towards this goal, we introduce Pit30M, a new image and LiDAR dataset with over 30 million frames, which is 10 to 100 times larger than those used in previous work. Pit30M is captured under diverse conditions (i.e., season, weather, time of the day, traffic), and provides accurate localization ground truth. We also automatically annotate our dataset with historical weather and astronomical data, as well as with image and LiDAR semantic segmentation as a proxy measure for occlusion. We benchmark multiple existing methods for image and LiDAR retrieval and, in the process, introduce a simple, yet effective convolutional network-based LiDAR retrieval method that is competitive with the state of the art. Our work provides, for the first time, a benchmark for sub-metre retrieval-based localization at city scale.</p>
			<!-- The dataset, additional experimental results, as well as more information about the sensors, calibration, and metadata, are available on the project website: this https URL</p> -->
		</div>
	</div>
</section>

<!--
<section class="container mx-auto px-4 py-12">
	<p class="text-lg mb-8">Brief description of the dataset, its purpose, and key features.</p>
	<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
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
-->

<!--
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
-->


<section class="container mx-auto px-4 py-12">
	<h2 class="text-3xl font-bold mb-8">High Quality LiDAR Data</h2>

	<div class="grid gap-6 h-screen">
		<div>
			<PointCloudViewer />
		</div>
	</div>
</section>


<section class="container mx-auto px-4 py-12">
	<h2 class="text-3xl font-bold mb-8">BibTeX</h2>
	<span class="text-lg">If you find our dataset useful, consider citing our work:</span>
	<div class="bg-gray-100 overflow-x-auto">
		<pre><code>
		{`
		@inproceedings{martinez2020pit30m,
			title={Pit30m: A benchmark for global localization in the age of self-driving cars},
			author={Martinez, Julieta and Doubov, Sasha and Fan, Jack and B{\^a}rsan, Ioan Andrei and Wang, Shenlong and 
				M{\'a}ttyus, Gell{\'e}rt and Urtasun, Raquel},
			booktitle={{IROS}},
			pages={4477--4484},
			year={2020},
			organization={IEEE}
		}
		`}
		</code></pre>
	</div>
</section>

<!--
<section class="container mx-auto px-4 py-12">
	<h2 class="text-3xl font-bold mb-8">Why Choose {datasetName}?</h2>
	<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
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
-->

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
					<a href="https://twitter.com/andreib" class="text-gray-600 hover:text-gray-900">
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
		display: inline-block;
		font-size: inherit;
		height: 1em;
		overflow: visible;
		vertical-align: -0.125em;
	}
</style>
