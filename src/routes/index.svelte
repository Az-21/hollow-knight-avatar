<script lang="ts">
	import { onMount } from 'svelte';
	import { face, eyes } from '../components/AvatarData.svelte';

	// Canvas width and height || WARNING: Do not change
	let canvasWidth: number = 512;
	let canvasHeight: number = 512;

	// Mount canvas
	let canvas: { getContext: (arg0: string) => any };
	onMount(() => {
		const ctx = canvas.getContext('2d');
		ctx.font = '30px Arial';
		ctx.fillStyle = '#aaa';
		ctx.textAlign = 'center';
		ctx.fillText('Az-21/hollow-knight-avatar/', canvasWidth / 2, canvasHeight / 2);
	});

	// Avatar data
	let faceId: number = 0;
	let eyesId: number = 0;

	function createImage() {
		const ctx = canvas.getContext('2d');
		const drawImage = (url: string) => {
			const image = new Image();
			image.src = url;
			image.onload = () => {
				ctx.drawImage(image, 0, 0);
			};
		};

		// Clear previous render -> prevent overlap
		ctx.clearRect(0, 0, canvasWidth, canvasHeight);

		// Draw knight
		drawImage(face[faceId]);
		drawImage(eyes[eyesId]);
	}
</script>

<!-- Canvas -->
<div class="mt-8 flex justify-center">
	<canvas
		class="border-8 border-green-500 rounded-lg"
		bind:this={canvas}
		width={canvasWidth}
		height={canvasHeight}
	/>
</div>

<!-- Avatar components -->
<div class="mt-8 flex justify-center space-x-4" on:change={() => createImage()}>
	<input
		type="number"
		class="bg-transparent ring-2 ring-blue-400"
		bind:value={faceId}
		min="0"
		max={face.length - 1}
	/>
	<input
		type="number"
		class="bg-transparent ring-2 ring-blue-400"
		bind:value={eyesId}
		min="0"
		max={eyes.length - 1}
	/>
</div>

<style>
	:global(body) {
		background-color: #1f2937;
		color: #fff;
	}
</style>
