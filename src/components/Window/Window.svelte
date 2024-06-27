<script lang="ts">
	import { draggable } from '@neodrag/svelte';
	import WindowHeader from './WindowHeader.svelte';
	import WindowFooter from './WindowFooter.svelte';

	export let title: string = '';
</script>

<section
	aria-label={title}
	class="absolute transform border border-gray-500 bg-gray-200 shadow-lg md:w-1/2"
	use:draggable
>
	<WindowHeader {title} />

	<div class="border-l-[16px] border-r-[16px] border-gray-500 p-4">
		<slot />
	</div>

	<WindowFooter />
</section>
