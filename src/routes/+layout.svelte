<script>
	import '../app.css';
	import Header from '../components/Header.svelte';
	import NavBar from '../components/NavBar.svelte';
	import Footer from '../components/Footer.svelte';
</script>

<div class="app flex h-full flex-col bg-gray-200">
	<Header />

	<div class="flex flex-grow flex-col sm:flex-row">
		<NavBar />

		<main class="flex-grow bg-gradient-to-b from-blue-500 via-blue-700 to-green-500">
			<slot />
		</main>
	</div>

	<Footer />
</div>
