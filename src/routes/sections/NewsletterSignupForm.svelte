<script>
	let email = '';
	let name = '';

	function handleSubmit() {
		console.log('Email:', email);
		console.log('Name:', name);
	}

	function closeWindow() {
		console.log('Close window');
	}

	function minimizeWindow() {
		console.log('Minimize window');
	}

	function maximizeWindow() {
		console.log('Maximize window');
	}
</script>

<section aria-label="Newsletter" class="border border-gray-500 bg-gray-200 shadow-lg md:w-1/2">
	<header class="flex items-center justify-between border-b border-gray-400 bg-gray-300 p-1">
		<button
			type="button"
			on:click={closeWindow}
			aria-label="Close"
			class="w-[16px] border border-gray-400"
		>
			<!-- Close icon or character -->
		</button>
		<h2 class="text-left text-base font-normal">Newsletter</h2>
		<div class="flex items-center justify-end space-x-2">
			<button
				type="button"
				on:click={minimizeWindow}
				aria-label="Minimize"
				class="w-[16px] border border-gray-400"
			>
				<!-- Minimize icon or character -->
			</button>
			<button
				type="button"
				on:click={maximizeWindow}
				aria-label="Maximize"
				class="w-[16px] border border-gray-400"
			>
				<!-- Maximize icon or character -->
			</button>
		</div>
	</header>
	<div class="border-l-[16px] border-r-[16px] border-gray-500 p-4">
		<form on:submit|preventDefault={handleSubmit} class="space-y-4">
			<div>
				<label for="email" class="mb-2 block text-sm font-bold text-gray-700">Email:</label>
				<input
					id="email"
					type="email"
					bind:value={email}
					required
					class="focus:shadow-outline-blue w-full border border-gray-600 px-3 py-2 text-sm leading-tight text-gray-700 shadow-none focus:outline-none"
				/>
			</div>
			<div>
				<label for="name" class="mb-2 block text-sm font-bold text-gray-700">Name:</label>
				<input
					id="name"
					type="text"
					bind:value={name}
					required
					class="focus:shadow-outline-blue w-full border border-gray-600 px-3 py-2 text-sm leading-tight text-gray-700 shadow-none focus:outline-none"
				/>
			</div>
			<button
				type="submit"
				class="focus:shadow-outline-blue full w-full bg-blue-600 px-4 py-2 font-bold text-white hover:bg-blue-700 focus:outline-none"
			>
				Sign Up
			</button>
		</form>
	</div>
	<footer class="h-2 border-t border-gray-500 bg-gray-200 p-2"></footer>
</section>

<style>
	/* Custom styles for shadow outline */
	.focus\:shadow-outline-blue:focus {
		box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.5);
	}
</style>
