<script lang="ts">
	import { onMount } from 'svelte';
	import { face, eyes } from '../components/AvatarData.svelte';
	import Selector from '../components/Selector.svelte';

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

	// Avatar componet ID data
	let faceId: number = 0;
	let eyesId: number = 0;

	// Avatar component y-position data
	let yFace: number = -10;
	let yEyes: number = 0;

	function createImage() {
		const ctx = canvas.getContext('2d');
		const drawImage = (url: string, yPosition: number) => {
			const image = new Image();
			image.src = url;
			image.onload = () => {
				ctx.drawImage(image, 0, yPosition);
			};
		};

		// Clear previous render
		ctx.clearRect(0, 0, canvasWidth, canvasHeight);

		// Draw knight
		drawImage(face[faceId], yFace);
		drawImage(eyes[eyesId], yEyes);
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
	<Selector
		componentName="Face"
		bind:componentId={faceId}
		componentCount={face.length - 1}
		bind:yPos={yFace}
	/>
	<Selector
		componentName="Eyes"
		bind:componentId={eyesId}
		componentCount={eyes.length - 1}
		bind:yPos={yEyes}
	/>
</div>

<style>
	:global(body) {
		background-color: #1f2937;
		color: #fff;
	}
</style>
