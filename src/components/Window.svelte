<script lang="ts">
	import { onMount } from 'svelte';
	import WindowHeader from './WindowHeader.svelte';

	let x = 0;
	let y = 0;
	let header: WindowHeader;
	let footer: HTMLElement;

	onMount(() => {
		const headerHeight = header.offsetHeight;
		const footerHeight = footer.offsetHeight;
		const { clientWidth, clientHeight } = document.documentElement;
		x = Math.floor(Math.random() * (clientWidth - window.innerWidth));
		y = Math.floor(Math.random() * (clientHeight - headerHeight - footerHeight) + headerHeight);
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

			// Limit the movement within the viewport
			if (x < 0) x = 0;
			if (x > window.innerWidth - node.offsetWidth) {
				x = window.innerWidth - node.offsetWidth;
			}
			if (y < header.offsetHeight) y = header.offsetHeight;
			if (y > window.innerHeight - node.offsetHeight - footer.offsetHeight) {
				y = window.innerHeight - node.offsetHeight - footer.offsetHeight;
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
	class="absolute transform border border-gray-500 bg-gray-200 shadow-lg md:w-1/2"
	style="transform: translate3d({x}px, {y}px, 0);"
>
	<WindowHeader bind:this={header} {title} />
	<div class="border-l-[16px] border-r-[16px] border-gray-500 p-4">
		<slot />
	</div>
	<footer bind:this={footer} class="h-2 border-t border-gray-500 bg-gray-200 p-2"></footer>
</section>
