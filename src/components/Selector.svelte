<script lang="ts">
	import Button from './Button.svelte';

	export let componentName: string;
	export let componentId: number;
	export let componentCount: number;
	export let yPos: number;
</script>

<div class="bg-gray-900 rounded-xl p-6">
	<div class="divide-y-2 divide-green-500">
		<div class="flex justify-between items-end">
			<p class="text-xl font-medium">Customize {componentName}</p>
			<Button text="View All" color="bg-blue-600" />
		</div>
		<p class="mt-2" />
	</div>
	<div class="mt-2 grid grid-cols-2 gap-x-8 gap-y-4 items-end">
		<!-- Row 1 -->
		<p class="font-thin text-lg">{componentName} ID</p>
		<input
			type="number"
			class="bg-transparent ring-2 ring-green-500 w-full h-8 flex text-center"
			bind:value={componentId}
			min="0"
			max={componentCount}
		/>

		<!-- Row 2 -->
		<p class="font-thin text-lg">Position</p>
		<div class="slidecontainer">
			<input type="range" min="-240" max="240" bind:value={yPos} class="slider w-full h-8" />
		</div>

		<!-- Row 3 -->
		<div on:click={() => (componentId = 0)}>
			<Button text="Transparent" color="bg-green-500" expand={true} />
		</div>
		<div on:click={() => (yPos = 0)}>
			<Button text="Reset" color="bg-green-500" expand={true} />
		</div>
	</div>
</div>

<style>
	.slidecontainer {
		width: 100%;
	}
	.slider {
		-webkit-appearance: none;
		appearance: none;
		width: 100%;
		background: #d3d3d3;
		outline: none;
		opacity: 1;
		-webkit-transition: 0.2s;
		transition: opacity 0.2s;
	}
	.slider:hover {
		opacity: 1;
	}

	.slider::-webkit-slider-thumb {
		-webkit-appearance: none;
		appearance: none;
		width: 20px;
		height: 40px;
		background: #2563eb;
		cursor: pointer;
		border-radius: 2px;
	}

	.slider::-moz-range-thumb {
		width: 25px;
		height: 25px;
		background: #2563eb;
		cursor: pointer;
	}
</style>
