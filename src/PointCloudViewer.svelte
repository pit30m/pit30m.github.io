<!-- PointCloudViewer.svelte -->
<script>
	import { onMount } from 'svelte';
	import * as THREE from 'three';
	import { PCDLoader } from 'three/examples/jsm/loaders/PCDLoader';
	import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls';

	let container;
	let scene, camera, renderer, points;
	let frameIndex = 1;
	let pointCloudFrames = [];

	let clock = new THREE.Clock();
	let delta = 0;

	let fps = 12;
	let interval = 1 / fps;

	let rotate_speed = 0;
	let fwd = true;

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

			let geometry = new THREE.BufferGeometry();
			
			const points_i = pointCloudFrames[i];

			// console.log(points_i)

			// in-place rotation
			points_i.geometry.rotateX(-Math.PI / 2);

			// set the colour of each point according to its height
			let points_xyz = points_i.geometry.attributes.position
			
			let positions = []
			let colors = []
			const color = new THREE.Color();

			for (let j=0; j<points_xyz.count * 3; j+=3) {
				let x = points_xyz.array[j]
				let y = points_xyz.array[j+1]
				let z = points_xyz.array[j+2]

				positions.push( x, y, z );
				
				const vx = ( x ) / 60;
				const vy = ( y + 4 ) / 4;
				const vz = ( z + 32) / 32;

				color.setRGB( vx, vy, vz, THREE.SRGBColorSpace );
				// color.setRGB( vx, vy, vz, THREE.LinearSRGBColorSpace );
				colors.push(color.r, color.g, color.b);
			}
			
			points_i.geometry.setAttribute('color', new THREE.Float32BufferAttribute( colors, 3 ))

			geometry.setAttribute( 'position', new THREE.Float32BufferAttribute( positions, 3 ) );
			geometry.setAttribute( 'color', new THREE.Float32BufferAttribute( colors, 3 ) );
			geometry.computeBoundingSphere();

			const material = new THREE.PointsMaterial( { size: 0.1, vertexColors: true } );
			let points_i_new = new THREE.Points(geometry, material)

			pointCloudFrames[i] = points_i_new
			// break
		}
		// points.setAttribute
		// scene.add(points);

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

			// console.log(fwd, frameIndex)

			if (frameIndex >= pointCloudFrames.length - 1) {
				fwd = !fwd
			}

			if (frameIndex == 1) {
				fwd = true
			}

			if (fwd) {
				frameIndex = (frameIndex + 1) % pointCloudFrames.length;
			} else {
				frameIndex = (frameIndex - 1) % pointCloudFrames.length;
			}

			points = pointCloudFrames[frameIndex];
			scene.add(points);

			controls.update();

			delta = delta % interval;

			renderer.render(scene, camera);
		}
	}
</script>

<div bind:this={container} class="w-full h-full" />
