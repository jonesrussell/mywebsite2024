<script lang="ts">
	import WindowButton from '../../components/WindowButton.svelte';

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

<section aria-label="Blog" class="border border-gray-500 bg-gray-200 shadow-lg md:w-1/2">
	<header class="flex h-2 items-center justify-between border-b border-gray-400 bg-gray-300 p-2">
		<WindowButton action={closeWindow} label="Close" />
		<h2 class="text-left text-base font-normal">Blog</h2>
		<div class="flex items-center justify-end space-x-2">
			<WindowButton action={minimizeWindow} label="Minimize" />
			<WindowButton action={maximizeWindow} label="Maximize" />
		</div>
	</header>
	<div class="border-l-[16px] border-r-[16px] border-gray-500 p-4">Blog</div>
	<footer class="h-2 border-t border-gray-500 bg-gray-200 p-2"></footer>
</section>
