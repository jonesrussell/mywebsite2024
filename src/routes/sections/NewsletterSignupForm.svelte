<script>
	let email = '';
	let name = '';

	function handleSubmit() {
		// Handle form submission logic here
		console.log('Email:', email);
		console.log('Name:', name);
	}
</script>

<section aria-label="Newsletter" class="flex flex-col items-center justify-center bg-gray-300 py-5">
	<div
		class="bg-gray-200 border border-gray-600 rounded px-8 pt-6 pb-8 mb-4 flex flex-col max-w-sm mx-auto"
	>
		<h2 class="mb-4 text-xl font-bold text-gray-700">Newsletter</h2>
		<form
			on:submit|preventDefault={handleSubmit}
			class="mb-4 md:flex md:flex-wrap md:justify-between"
		>
			<div class="mb-4 md:mr-2 md:mb-0">
				<label class="block mb-2 text-sm font-bold text-gray-700" for="email"> Email: </label>
				<input
					class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border border-gray-600 rounded shadow-none focus:outline-none focus:shadow-none"
					id="email"
					type="email"
					bind:value={email}
					required
					aria-required="true"
				/>
			</div>
			<div class="mb-4 md:ml-2">
				<label class="block mb-2 text-sm font-bold text-gray-700" for="name"> Name: </label>
				<input
					class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border border-gray-600 rounded shadow-none focus:outline-none focus:shadow-none"
					id="name"
					type="text"
					bind:value={name}
					required
					aria-required="true"
				/>
			</div>
			<div class="mb-4">
				<button
					class="w-full px-4 py-2 font-bold text-white bg-gray-600 rounded-full hover:bg-gray-700 focus:outline-none focus:shadow-none"
					type="submit"
					aria-label="Sign Up"
				>
					Sign Up
				</button>
			</div>
		</form>
	</div>
</section>
