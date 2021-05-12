<script lang="ts">
	import { face, eyes } from '../components/AvatarData.svelte';

	export let center: string = 'flex w-4/5 mx-auto';
	export let spacing: string = 'mt-8';

	export let cols = 5;
	export let category: number = 0;

	export let faceId: number = 0;
	export let eyesId: number = 0;
</script>

<div class="{center} {spacing}">
	<p class="ml-8 text-2xl font-thin">Variants available</p>
</div>

<div class="{center} bg-gray-900 flex justify-around rounded-xl ring-2 ring-blue-400">
	<!-- Face -->
	{#if category === 0}
		{#each face as _, index}
			{#if index % cols === 0}
				<div class="flex space-x-2">
					{#each Array(cols) as _, j}
						{#if face[(index / cols) * cols + j]}
							<div on:click={() => (faceId = (index / cols) * cols + j)}>
								<img
									class="w-32 h-32 m-2 rounded-lg ring-1 shadow ring-blue-400"
									src={face[(index / cols) * cols + j]}
									alt={`face-${face[(index / cols) * cols + j]}`}
								/>
							</div>
						{/if}
					{/each}
				</div>
			{/if}
		{/each}

		<!-- Eyes -->
	{:else if category === 1}
		{#each eyes as _, index}
			{#if index % cols === 0}
				<div class="flex space-x-2">
					{#each Array(cols) as _, j}
						{#if eyes[(index / cols) * cols + j]}
							<div on:click={() => (eyesId = (index / cols) * cols + j)}>
								<img
									class="w-32 h-32 m-2 rounded-lg ring-1 shadow ring-blue-400"
									src={eyes[(index / cols) * cols + j]}
									alt={`eyes-${eyes[(index / cols) * cols + j]}`}
								/>
							</div>
						{/if}
					{/each}
				</div>
			{/if}
		{/each}
	{:else}
		<p class="text-red-500 text-lg">
			ERROR: uncaught component number. Fix DisplayComponents.svelte
		</p>
	{/if}
</div>
