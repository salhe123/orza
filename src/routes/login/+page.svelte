<script lang="ts">
	import { goto } from '$app/navigation';
	import AuthCard from '$lib/components/auth/auth-card.svelte';
	import AuthInput from '$lib/components/auth/auth-input.svelte';
	import AuthButton from '$lib/components/auth/auth-button.svelte';
	import SocialButton from '$lib/components/auth/social-button.svelte';

	let email = $state('');
	let password = $state('');
	let isLoading = $state(false);

	async function handleLogin(e: Event) {
		e.preventDefault();
		isLoading = true;

		// TODO: Implement actual login logic
		console.log('[v0] Login attempt:', { email, password });

		// Simulate API call
		setTimeout(() => {
			isLoading = false;
			// goto('/dashboard'); // Navigate after successful login
		}, 1000);
	}

	function handleGoogleLogin() {
		console.log('[v0] Google login clicked');
		// TODO: Implement Google OAuth
	}

	function handleAppleLogin() {
		console.log('[v0] Apple login clicked');
		// TODO: Implement Apple OAuth
	}

	function goHome() {
		goto('/');
	}
</script>

<svelte:head>
	<title>Login - Orza</title>
</svelte:head>

<div class="relative flex min-h-screen flex-col items-center justify-start bg-background p-4 pt-16">
	<!-- Logo at Top Above AuthCard -->
	<div class="absolute top-4 left-1/2 -translate-x-1/2 transform">
		<button onclick={goHome} class="flex items-center" aria-label="Go Home">
			<img src="/assets/login.png" alt="Orza Logo" class="h-20 w- object-contain" />
		</button>
	</div>

	<AuthCard>
		<div class="flex flex-col items-center gap-6">
			<h1 class="text-2xl font-semibold text-foreground">Login</h1>

			<form onsubmit={handleLogin} class="w-full space-y-4">
				<AuthInput
					type="email"
					placeholder="Email"
					bind:value={email}
					required
					autocomplete="email"
				/>

				<AuthInput
					type="password"
					placeholder="Password"
					bind:value={password}
					required
					autocomplete="current-password"
				/>

				<div class="flex justify-end">
					<a
						href="/forgot-password"
						class="text-sm text-muted-foreground transition-colors hover:text-foreground"
					>
						Forgot password?
					</a>
				</div>

				<AuthButton type="submit" loading={isLoading}>
					Log In
					<svg
						class="ml-2 h-4 w-4"
						fill="none"
						stroke="currentColor"
						viewBox="0 0 24 24"
						xmlns="http://www.w3.org/2000/svg"
					>
						<path
							stroke-linecap="round"
							stroke-linejoin="round"
							stroke-width="2"
							d="M13 7l5 5m0 0l-5 5m5-5H6"
						/>
					</svg>
				</AuthButton>
			</form>

			<div class="flex w-full items-center gap-4">
				<div class="h-px flex-1 bg-border"></div>
				<span class="text-sm text-muted-foreground">OR</span>
				<div class="h-px flex-1 bg-border"></div>
			</div>

			<div class="w-full space-y-3">
				<SocialButton provider="google" onclick={handleGoogleLogin}>
					Log in with Google
				</SocialButton>

				<SocialButton provider="apple" onclick={handleAppleLogin}>Log in with Apple</SocialButton>
			</div>

			<p class="text-sm text-muted-foreground">
				Don't have an account?
				<a href="/signup" class="font-medium text-foreground hover:underline">Sign Up</a>
			</p>
		</div>
	</AuthCard>
</div>
