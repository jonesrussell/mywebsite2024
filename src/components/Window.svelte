<script lang="ts">
	import WindowHeader from './WindowHeader.svelte';

	export let title: string = '';
</script>

<section aria-label={title} class="border border-gray-500 bg-gray-200 shadow-lg md:w-1/2">
	<WindowHeader {title} />
	<div class="border-l-[16px] border-r-[16px] border-gray-500 p-4">
		<slot />
	</div>
	<footer class="h-2 border-t border-gray-500 bg-gray-200 p-2"></footer>
</section>
