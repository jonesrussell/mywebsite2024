<script lang="ts">
	import WindowHeader from './WindowHeader.svelte';

	function draggable(node: HTMLElement) {
		let x: number;
		let y: number;

		function handleMousedown(event: { clientX: number; clientY: number }) {
			x = event.clientX;
			y = event.clientY;

			node.dispatchEvent(
				new CustomEvent('dragstart', {
					detail: { x, y }
				})
			);

			window.addEventListener('mousemove', handleMousemove);
			window.addEventListener('mouseup', handleMouseup);
		}

		function handleMousemove(event: { clientX: number; clientY: number }) {
			const dx = event.clientX - x;
			const dy = event.clientY - y;

			node.style.transform = `translate(${dx}px, ${dy}px)`;

			node.dispatchEvent(
				new CustomEvent('dragmove', {
					detail: { x: event.clientX, y: event.clientY }
				})
			);
		}

		function handleMouseup(event: { clientX: number; clientY: number }) {
			x = event.clientX;
			y = event.clientY;

			node.dispatchEvent(
				new CustomEvent('dragend', {
					detail: { x, y }
				})
			);

			window.removeEventListener('mousemove', handleMousemove);
			window.removeEventListener('mouseup', handleMouseup);
		}

		node.addEventListener('mousedown', handleMousedown);

		return {
			destroy() {
				node.removeEventListener('mousedown', handleMousedown);
			}
		};
	}

	export let title: string = '';
</script>

<section
	use:draggable
	aria-label={title}
	class="border border-gray-500 bg-gray-200 shadow-lg md:w-1/2"
>
	<WindowHeader {title} />
	<div class="border-l-[16px] border-r-[16px] border-gray-500 p-4">
		<slot />
	</div>
	<footer class="h-2 border-t border-gray-500 bg-gray-200 p-2"></footer>
</section>
