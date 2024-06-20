<script lang="ts">
	import { onMount } from 'svelte';
	import WindowHeader from './WindowHeader.svelte';
	import WindowFooter from './WindowFooter.svelte';

	let x = 0;
	let y = 0;
	let header: HTMLElement;
	let footer: HTMLElement;

	function calculateInitialPosition() {
		const headerHeight = header.offsetHeight;
		const footerHeight = footer.offsetHeight;
		const { clientWidth, clientHeight } = document.documentElement;
		x = Math.floor(Math.random() * (clientWidth - header.offsetWidth));
		y = Math.floor(Math.random() * (clientHeight - headerHeight - footerHeight) + headerHeight);
		console.log(`Initial position: x=${x}, y=${y}`);
	}

	function makeElementDraggable(node: HTMLElement) {
		let mouseX: number;
		let mouseY: number;

		function startDragging(event: MouseEvent) {
			mouseX = event.clientX - node.getBoundingClientRect().left;
			mouseY = event.clientY - node.getBoundingClientRect().top;
			window.addEventListener('mousemove', drag);
			window.addEventListener('mouseup', stopDragging);
		}

		function drag(event: MouseEvent) {
			x = event.clientX - mouseX;
			y = event.clientY - mouseY;
			limitMovementWithinViewport(node);
			node.style.transform = `translate3d(${x}px, ${y}px, 0)`;
		}

		function stopDragging() {
			window.removeEventListener('mousemove', drag);
			window.removeEventListener('mouseup', stopDragging);
		}

		function limitMovementWithinViewport(node: HTMLElement) {
			if (x < 0) x = 0;
			if (x > window.innerWidth - node.offsetWidth) {
				x = window.innerWidth - node.offsetWidth;
			}
			if (y < header.offsetHeight) y = header.offsetHeight;
			if (y > window.innerHeight - node.offsetHeight - footer.offsetHeight) {
				y = window.innerHeight - node.offsetHeight - footer.offsetHeight;
			}
		}

		node.addEventListener('mousedown', startDragging);

		return {
			destroy() {
				node.removeEventListener('mousedown', startDragging);
			}
		};
	}

	export let title: string = '';

	onMount(calculateInitialPosition);
</script>

<section
	use:makeElementDraggable
	aria-label={title}
	class="absolute transform border border-gray-500 bg-gray-200 shadow-lg md:w-1/2"
	style="transform: translate3d({x}px, {y}px, 0);"
>
	<div bind:this={header}>
		<WindowHeader {title} />
	</div>

	<div class="border-l-[16px] border-r-[16px] border-gray-500 p-4">
		<slot />
	</div>

	<div bind:this={footer}>
		<WindowFooter />
	</div>
</section>
