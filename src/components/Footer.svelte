<script lang="ts">
	export let center: string = 'flex w-4/5 mx-auto';
	export let spacing: string = 'mt-8';
</script>

<div class="{spacing} {center} flex overflow-hidden bg-gray-700 rounded-lg shadow-md">
	<div class="flex items-center justify-center w-24 bg-blue-500">
		<svg
			class="w-6 h-6 text-white fill-current"
			viewBox="0 0 40 40"
			xmlns="http://www.w3.org/2000/svg"
		>
			<path
				d="M20 3.33331C10.8 3.33331 3.33337 10.8 3.33337 20C3.33337 29.2 10.8 36.6666 20 36.6666C29.2 36.6666 36.6667 29.2 36.6667 20C36.6667 10.8 29.2 3.33331 20 3.33331ZM21.6667 28.3333H18.3334V25H21.6667V28.3333ZM21.6667 21.6666H18.3334V11.6666H21.6667V21.6666Z"
			/>
		</svg>
	</div>

	<div class="px-4 py-2 -mx-3">
		<div class="mx-3">
			<span class="font-bold text-blue-500">Disclaimer</span>
			<p class="text-sm text-gray-100">
				Hollow Knight is © Copyright {new Date().getFullYear()} Team Cherry.
			</p>
		</div>
	</div>
</div>

<div class="mt-5 bg-gray-900  py-5 shadow-lg">
	<div class="{center} text-white flex items-end justify-between">
		<div class="font-medium">
			<a class="px-2 hover:text-green-300" target="_blank" href="https://github.com/Az-21/">
				Made by Az-21
			</a>
		</div>
		<div class="font-medium">
			<a
				class="px-2 hover:text-green-300"
				target="_blank"
				href="https://github.com/Az-21/hollow-knight-avatar/issues"
			>
				🐞 Report Bug
			</a>
		</div>
		<div class="font-medium">
			<a
				class="px-2 hover:text-green-300"
				target="_blank"
				href="https://github.com/Az-21/hollow-knight-avatar/stargazers"
			>
				★ On GitHub
			</a>
		</div>
	</div>
</div>
