<script lang="ts">
	import { onMount } from 'svelte';
	import WindowHeader from './WindowHeader.svelte';

	let x = 0;
	let y = 0;
	const footerHeight = 50; // Adjust according to your footer's height

	onMount(() => {
		const { clientWidth, clientHeight } = document.documentElement;
		x = Math.floor(Math.random() * clientWidth);
		y = Math.floor(Math.random() * (clientHeight - footerHeight));
	});

	function draggable(node: HTMLElement) {
		let mouseX: number;
		let mouseY: number;

		function handleMousedown(event: MouseEvent) {
			mouseX = event.clientX - node.getBoundingClientRect().left;
			mouseY = event.clientY - node.getBoundingClientRect().top;

			window.addEventListener('mousemove', handleMousemove);
			window.addEventListener('mouseup', handleMouseup);
		}

		function handleMousemove(event: MouseEvent) {
			x = event.clientX - mouseX;
			y = event.clientY - mouseY;

			// Limit the movement within the viewport height minus the footer height
			if (y < 0) y = 0;
			if (y > window.innerHeight - node.offsetHeight - footerHeight) {
				y = window.innerHeight - node.offsetHeight - footerHeight;
			}

			node.style.transform = `translate3d(${x}px, ${y}px, 0)`;
		}

		function handleMouseup() {
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
	style="position: absolute; transform: translate3d({x}px, {y}px, 0);"
>
	<WindowHeader {title} />
	<div class="border-l-[16px] border-r-[16px] border-gray-500 p-4">
		<slot />
	</div>
	<footer class="h-2 border-t border-gray-500 bg-gray-200 p-2"></footer>
</section>
