<script>
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
	import NewsletterSignupForm from './sections/NewsletterSignupForm.svelte';
	import SabrinasShows from './sections/SabrinasShows.svelte';
	import AppearanceCards from './sections/AppearanceCards.svelte';
	import PersonalityTraitsCards from './sections/PersonalityTraitsCards.svelte';
	import Testimonials from './sections/Testimonials.svelte';
	import Benefits from './sections/Benefits.svelte';
	import Features from './sections/Features.svelte';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>
		<span class="welcome">
			<picture>
				<source srcset={welcome} type="image/webp" />
				<img src={welcome_fallback} alt="Welcome" />
			</picture>
		</span>

		to your new<br />SvelteKit app
	</h1>

	<NewsletterSignupForm />
  <SabrinasShows />
  <AppearanceCards />
  <PersonalityTraitsCards />
  <Testimonials />
  <Benefits />
  <Features />
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}

	h1 {
		width: 100%;
	}

	.welcome {
		display: block;
		position: relative;
		width: 100%;
		height: 0;
		padding: 0 0 calc(100% * 495 / 2048) 0;
	}

	.welcome img {
		position: absolute;
		width: 100%;
		height: 100%;
		top: 0;
		display: block;
	}
</style>
