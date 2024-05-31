<script>
	import NewsletterSignupForm from './sections/NewsletterSignupForm.svelte';
	import SabrinasShows from './sections/SabrinasShows.svelte';
	import AppearanceCards from './sections/AppearanceCards.svelte';
	import PersonalityTraitsCards from './sections/PersonalityTraitsCards.svelte';
	import Testimonials from './sections/Testimonials.svelte';
	import Benefits from './sections/Benefits.svelte';
	import Features from './sections/Features.svelte';
</script>

<svelte:head>
	<title>Russell Jones | Home</title>
	<meta name="description" content="Russell Jones" />
</svelte:head>

<section>
	<!-- Window 1 -->
	<div class="bg-white rounded-lg shadow-lg p-4 m-4">
		<button class="bg-blue-500 text-white px-2 py-1 rounded-md">Open</button>
	</div>

	<!-- Window 2 -->
	<div class="bg-white rounded-lg shadow-lg p-4 m-4">
		<button class="bg-blue-500 text-white px-2 py-1 rounded-md">Open</button>
	</div>

	<NewsletterSignupForm />
	<SabrinasShows />
	<AppearanceCards />
	<PersonalityTraitsCards />
	<Testimonials />
	<Benefits />
	<Features />
</section>
