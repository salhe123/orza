<script lang="ts">
	interface Props {
		type?: 'button' | 'submit';
		loading?: boolean;
		onclick?: () => void;
		children: any;
	}

	let { type = 'button', loading = false, onclick, children }: Props = $props();
</script>

<button
	{type}
	{onclick}
	disabled={loading}
	class="w-full px-4 py-3 bg-[hsl(258,100%,65%)] hover:bg-[hsl(258,100%,60%)] text-white font-medium rounded-lg transition-all duration-200 flex items-center justify-center gap-2 disabled:opacity-50 disabled:cursor-not-allowed shadow-md hover:shadow-lg"
>
	{#if loading}
		<svg class="animate-spin h-5 w-5" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24">
			<circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle>
			<path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"></path>
		</svg>
		<span>Loading...</span>
	{:else}
		{@render children()}
	{/if}
</button>
