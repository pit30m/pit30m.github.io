<!-- PointCloudViewer.svelte -->
<script>
	import { onMount } from 'svelte';
	import * as THREE from 'three';
	import { PCDLoader } from 'three/examples/jsm/loaders/PCDLoader';
	import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';

	let container;
	let scene, camera, renderer, points;
	let frameIndex = 0;
	let pointCloudFrames = [];

	let clock = new THREE.Clock();
	let delta = 0;

	let fps = 10;
	let interval = 1 / fps;

	let rotate_speed = 10;

	let r = 20;

	let controls;

	onMount(async () => {
		await loadPointCloudFrames();
		init();
		animate();
	});

	async function loadPointCloudFrames() {
		const loader = new PCDLoader();
		const pcdUrls = [
			// List your PCD file URLs here
			'00.pcd',
			'01.pcd',
			'02.pcd',
			'03.pcd',
			'04.pcd',
			'05.pcd',
			'06.pcd',
			'07.pcd',
			'08.pcd',
			'09.pcd'
		];

		pointCloudFrames = await Promise.all(
			pcdUrls.map(
				(url) =>
					new Promise((resolve) => {
						loader.load(url, (points) => {
							resolve(points);
						});
					})
			)
		);
	}

	function init() {
		scene = new THREE.Scene();
		camera = new THREE.PerspectiveCamera(75, container.clientWidth / container.clientHeight, 0.1, 1000);
		renderer = new THREE.WebGLRenderer();
		renderer.setSize(container.clientWidth, container.clientHeight);
		container.appendChild(renderer.domElement);

		// rotate each mesh by 90 degrees on the x axis
		for (let i = 0; i < pointCloudFrames.length; i++) {
			console.log(i);
			points = pointCloudFrames[i];
			points.geometry.rotateX(-Math.PI / 2);
		}
		scene.add(points);

		controls = new OrbitControls(camera, renderer.domElement);
		controls.autoRotate = true;
		controls.autoRotateSpeed = rotate_speed;

		camera.position.set(r, r, r);
		controls.update();
	}

	function animate() {
		requestAnimationFrame(animate);

		delta += clock.getDelta();

		if (delta > interval) {
			// Update the point cloud frame
			scene.remove(points);
			frameIndex = (frameIndex + 1) % pointCloudFrames.length;
			points = pointCloudFrames[frameIndex];
			scene.add(points);

			controls.update();

			delta = delta % interval;

			renderer.render(scene, camera);
		}
	}
</script>

<div bind:this={container} class="w-full h-full" />
