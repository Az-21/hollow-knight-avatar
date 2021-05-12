<script lang="ts">
	import { onMount } from 'svelte';
	import { face, eyes } from '../components/AvatarData.svelte';
	import Navbar from '../components/Navbar.svelte';
	import Selector from '../components/Selector.svelte';
	import DisplayComponents from '../components/DisplayComponents.svelte';
	import Footer from '../components/Footer.svelte';

	// Page dimension constants
	export let center: string = 'flex w-4/5 mx-auto';
	export let spacing: string = 'mt-8';

	// Canvas width and height || WARNING: Do not change
	let canvasWidth: number = 512;
	let canvasHeight: number = 512;

	// Mount canvas
	let canvas: { getContext: (arg0: string) => any };
	onMount(() => {
		const ctx = canvas.getContext('2d');
		ctx.font = '20px Arial';
		ctx.fillStyle = '#aaa';
		ctx.textAlign = 'center';
		ctx.fillText('github/Az-21/hollow-knight-avatar/', canvasWidth / 2, canvasHeight / 2);
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

	// Display all available variants within a category
	let category = 0;
	function changeCategory(num: number) {
		category = num;
	}
</script>

<Navbar />

<div class="{center} {spacing} flex md:flex-col lg:flex-row justify-between space-x-5">
	<!-- Canvas -->
	<div class="flex justify-center">
		<canvas
			class="border-8 border-green-500 rounded-lg"
			bind:this={canvas}
			width={canvasWidth}
			height={canvasHeight}
		/>
	</div>

	<!-- Avatar components -->
	<div>
		<!-- Row 1: Face + Eyes -->
		<div class="flex justify-center space-x-4" on:click={() => createImage()}>
			<!-- Face -->
			<div on:click={() => changeCategory(0)}>
				<Selector
					componentName="Face"
					bind:componentId={faceId}
					componentCount={face.length - 1}
					bind:yPos={yFace}
				/>
			</div>

			<!-- Eyes -->
			<div on:click={() => changeCategory(1)}>
				<Selector
					componentName="Eyes"
					bind:componentId={eyesId}
					componentCount={eyes.length - 1}
					bind:yPos={yEyes}
				/>
			</div>
		</div>
	</div>
</div>

<!-- View components -->
<div on:click={() => createImage()}>
	<DisplayComponents {category} bind:faceId bind:eyesId />
</div>

<!-- Footer -->
<Footer />

<style>
	:global(body) {
		background-color: #1f2937;
		color: #fff;
	}
</style>
