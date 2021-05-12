<script lang="ts">
	export let componentName: string;
	export let componentId: number;
	export let componentCount: number;
	export let yPos: number;
</script>

<div>
	<p>{componentName}</p>
	<input
		type="number"
		class="bg-transparent ring-2 ring-blue-400 w-24 flex text-center"
		bind:value={componentId}
		min="0"
		max={componentCount}
	/>
	<div class="slidecontainer">
		<input type="range" min="-256" max="256" bind:value={yPos} class="slider w-24" />
	</div>
</div>
