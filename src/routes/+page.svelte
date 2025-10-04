<script lang="ts">
	import { goto } from '$app/navigation';
</script>

<svelte:head>
	<title>Welcome - Orza</title>
</svelte:head>

<div class="min-h-screen flex flex-col items-center justify-center bg-background p-4">
	<div class="text-center space-y-6">
		<div class="w-24 h-24 mx-auto">
			<img src="/assets/login.png" alt="Orza Logo" class="w-full h-full object-contain" />
		</div>
		
		<h1 class="text-4xl font-bold text-foreground">Welcome to Orza</h1>
		<p class="text-lg text-muted-foreground max-w-md">
			Get started by logging in or creating a new account
		</p>

		<div class="flex flex-col sm:flex-row gap-4 justify-center pt-4">
			<a
				href="/login"
				class="px-8 py-3 bg-[hsl(258,100%,65%)] hover:bg-[hsl(258,100%,60%)] text-white font-medium rounded-lg transition-all duration-200 shadow-md hover:shadow-lg"
			>
				Log In
			</a>
			<a
				href="/signup"
				class="px-8 py-3 bg-background border border-input hover:bg-accent hover:text-accent-foreground text-foreground font-medium rounded-lg transition-all duration-200 shadow-sm hover:shadow"
			>
				Sign Up
			</a>
		</div>
	</div>
</div>
