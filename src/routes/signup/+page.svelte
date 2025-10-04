<script lang="ts">
	import { goto } from '$app/navigation';
	import AuthCard from '$lib/components/auth/auth-card.svelte';
	import AuthInput from '$lib/components/auth/auth-input.svelte';
	import AuthButton from '$lib/components/auth/auth-button.svelte';
	import SocialButton from '$lib/components/auth/social-button.svelte';

	let firstName = $state('');
	let lastName = $state('');
	let email = $state('');
	let password = $state('');
	let agreeToTerms = $state(false);
	let isLoading = $state(false);

	async function handleSignup(e: Event) {
		e.preventDefault();
		isLoading = true;

		// TODO: Implement actual signup logic
		console.log('[v0] Signup attempt:', { firstName, lastName, email, password, agreeToTerms });

		// Simulate API call
		setTimeout(() => {
			isLoading = false;
			// goto('/dashboard'); // Navigate after successful signup
		}, 1000);
	}

	function handleGoogleSignup() {
		console.log('[v0] Google signup clicked');
		// TODO: Implement Google OAuth
	}

	function handleAppleSignup() {
		console.log('[v0] Apple signup clicked');
		// TODO: Implement Apple OAuth
	}

	function goHome() {
		goto('/');
	}
</script>

<svelte:head>
	<title>Sign Up - Orza</title>
</svelte:head>

<div class="min-h-screen flex items-center justify-center bg-background p-4 relative">
	<div class="absolute top-4 left-4">
		<button onclick={goHome} class="flex items-center gap-2" aria-label="Go Home">
			<img src="/assets/logo.png" alt="Orza Logo" class="w-[117px] h-[41px] object-contain" />
		</button>
	</div>

	<button onclick={goHome} class="absolute top-4 right-4 p-2 hover:bg-muted rounded-lg transition-colors" aria-label="Go Home">
		<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="text-foreground">
			<path d="m3 9 9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/>
			<polyline points="9 22 9 12 15 12 15 22"/>
		</svg>
	</button>

	<div class="w-full max-w-6xl flex items-center justify-between gap-12">
		<AuthCard>
			<div class="flex flex-col items-center gap-6">
				<h1 class="text-2xl font-semibold text-foreground">Create a new account</h1>

				<form onsubmit={handleSignup} class="w-full space-y-4">
					<div class="grid grid-cols-2 gap-3">
						<AuthInput
							type="text"
							placeholder="First Name"
							bind:value={firstName}
							required
							autocomplete="given-name"
						/>

						<AuthInput
							type="text"
							placeholder="Last Name"
							bind:value={lastName}
							required
							autocomplete="family-name"
						/>
					</div>

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
						autocomplete="new-password"
					/>

					<label class="flex items-start gap-2 cursor-pointer">
						<input
							type="checkbox"
							bind:checked={agreeToTerms}
							required
							class="mt-1 w-4 h-4 rounded border-input bg-background text-primary focus:ring-2 focus:ring-ring focus:ring-offset-2"
						/>
						<span class="text-sm text-muted-foreground">
							I agree to the Orza <a href="/terms" class="text-primary hover:underline">Terms of Use</a>
							and
							<a href="/privacy" class="text-primary hover:underline">Privacy policy</a>
						</span>
					</label>

					<AuthButton type="submit" loading={isLoading}>Join Now</AuthButton>
				</form>

				<div class="w-full flex items-center gap-4">
					<div class="flex-1 h-px bg-border"></div>
					<span class="text-sm text-muted-foreground">OR</span>
					<div class="flex-1 h-px bg-border"></div>
				</div>

				<div class="w-full space-y-3">
					<SocialButton provider="google" onclick={handleGoogleSignup}>
						Sign Up with Google
					</SocialButton>

					<SocialButton provider="apple" onclick={handleAppleSignup}>
						Sign Up with Apple
					</SocialButton>
				</div>

				<p class="text-sm text-muted-foreground">
					Already have an account?
					<a href="/login" class="text-foreground font-medium hover:underline">Log In</a>
				</p>
			</div>
		</AuthCard>

		<div class="hidden lg:block w-full max-w-sm text-right">
			<div>
				<h2 class="text-3xl font-bold text-foreground">30,000+ clients</h2>
				<p class="text-xl font-semibold text-foreground mt-1">are getting more replies!</p>
				<p class="text-sm text-muted-foreground mt-6 leading-relaxed">
					Unlock the power of lorem ipsum dolor sit amet. This is dummy text the lazy red fox jumped over the fence.
				</p>
			</div>
		</div>
	</div>
</div>
