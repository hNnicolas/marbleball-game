<script lang="ts">
	import Button from '$lib/components/ui/button/button.svelte';
	import { gameState } from '$lib/gamestate';
	import { slide } from 'svelte/transition';

	let classes = '';

	export let backButton = false;

	export let credits = false;

	export { classes as class };
</script>

<div
	transition:slide={{ duration: 200 }}
	class="pointer-events-auto rounded-t-xl ring-1 ring-white/50 shadow-xl bg-gradient-to-tr from-white/30 to-white/10 backdrop-blur-sm my-blur w-full max-w-xl relative px-5 sm:px-10 py-5 sm:py-10 {classes}"
>
	{#if backButton}
		<Button
			variant="custom"
			size="none"
			on:click={() => {
				$gameState = 'menu';
			}}
			class="absolute top-2 left-2 "
		>
			<svg
				xmlns="http://www.w3.org/2000/svg"
				viewBox="0 0 24 24"
				fill="currentColor"
				class="w-6 h-auto"
			>
				<path
					d="M11.47 3.841a.75.75 0 0 1 1.06 0l8.69 8.69a.75.75 0 1 0 1.06-1.061l-8.689-8.69a2.25 2.25 0 0 0-3.182 0l-8.69 8.69a.75.75 0 1 0 1.061 1.06l8.69-8.689Z"
				/>
				<path
					d="m12 5.432 8.159 8.159c.03.03.06.058.091.086v6.198c0 1.035-.84 1.875-1.875 1.875H15a.75.75 0 0 1-.75-.75v-4.5a.75.75 0 0 0-.75-.75h-3a.75.75 0 0 0-.75.75V21a.75.75 0 0 1-.75.75H5.625a1.875 1.875 0 0 1-1.875-1.875v-6.198a2.29 2.29 0 0 0 .091-.086L12 5.432Z"
				/>
			</svg>
		</Button>
	{/if}

	{#if credits}
		<div class="absolute bottom-2 right-2 text-xs">
			<a
				href="https://github.com/hNnicolas/marbleball-game"
				target="_blank"
				class="text-neutral-400 hover:text-neutral-500 flex items-center"
			>
				<span class="sr-only">Github</span>
				<svg class="h-6 w-6 ml-1" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
					<path
						fill-rule="evenodd"
						d="M12 2C6.477 2 2 6.484 2 12.017c0 4.425 2.865 8.18 6.839 9.504.5.092.682-.217.682-.483 0-.237-.008-.868-.013-1.703-2.782.605-3.369-1.343-3.369-1.343-.454-1.158-1.11-1.466-1.11-1.466-.908-.62.069-.608.069-.608 1.003.07 1.531 1.032 1.531 1.032.892 1.53 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.113-4.555-4.951 0-1.093.39-1.988 1.029-2.688-.103-.253-.446-1.272.098-2.65 0 0 .84-.27 2.75 1.026A9.564 9.564 0 0112 6.844c.85.004 1.705.115 2.504.337 1.909-1.296 2.747-1.027 2.747-1.027.546 1.379.202 2.398.1 2.651.64.7 1.028 1.595 1.028 2.688 0 3.848-2.339 4.695-4.566 4.943.359.309.678.92.678 1.855 0 1.338-.012 2.419-.012 2.747 0 .268.18.58.688.482A10.019 10.019 0 0022 12.017C22 6.484 17.522 2 12 2z"
						clip-rule="evenodd"
					/>
				</svg>
			</a>
		</div>
	{/if}

	<slot />
</div>
