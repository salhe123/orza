<script lang="ts">
		import type { FullAutoFill } from "svelte/elements";

	interface Props {
		type?: 'text' | 'email' | 'password';
		placeholder?: string;
		value?: string;
		required?: boolean;
		autocomplete?: FullAutoFill | null | undefined; 
	}

	let { type = 'text', placeholder = '', value = $bindable(''), required = false, autocomplete }: Props = $props();
</script>

<input
	{type}
	{placeholder}
	bind:value
	{required}
	autocomplete={autocomplete || undefined}
	class="w-full px-4 py-3 bg-background border border-input rounded-lg text-foreground placeholder:text-muted-foreground focus:outline-none focus:ring-2 focus:ring-ring focus:border-transparent transition-all"
/>