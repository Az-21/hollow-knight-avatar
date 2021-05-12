<script lang="ts">
	import Button from './Button.svelte';

	export let componentName: string;
	export let componentId: number;
	export let componentCount: number;
	export let yPos: number;
</script>

<div class="bg-gray-900 rounded-xl p-6">
	<div class="divide-y-2 divide-blue-600">
		<p class="text-lg font-medium">Customize {componentName}</p>
		<p />
	</div>
	<div class="mt-2 grid grid-cols-2 gap-x-8 gap-y-4">
		<!-- Row 1 -->
		<p class="font-thin items-end">{componentName} ID</p>
		<input
			type="number"
			class="bg-transparent ring-2 ring-blue-600 w-full flex text-center"
			bind:value={componentId}
			min="0"
			max={componentCount}
		/>

		<!-- Row 2 -->
		<p>Position</p>
		<div class="slidecontainer">
			<input type="range" min="-240" max="240" bind:value={yPos} class="slider w-full" />
		</div>

		<!-- Row 3 -->
		<div on:click={() => (componentId = 0)}>
			<Button text="Transparent" color="bg-blue-600" expand={true} />
		</div>

		<div on:click={() => (yPos = 0)}>
			<Button text="Reset" color="bg-blue-600" expand={true} />
		</div>
	</div>
</div>
