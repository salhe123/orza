<script lang="ts">
	let { children } = $props();
</script>

<div
	class="w-full max-w-md bg-card border border-border rounded-lg shadow-lg p-8 md:p-10 animate-in fade-in-50 duration-500"
>
	{@render children()}
</div>
