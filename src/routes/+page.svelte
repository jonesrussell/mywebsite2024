<script>
	import NewsletterSignupForm from './sections/NewsletterSignupForm.svelte';
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
	<NewsletterSignupForm />
	<AppearanceCards />
	<PersonalityTraitsCards />
	<Testimonials />
	<Benefits />
	<Features />
</section>
