<script>
	import '../app.css';
	import { page } from '$app/stores';
	import logo from '$lib/images/rej-logo.png';
	import github from '$lib/images/github.svg';
	import { base } from '$app/paths';
</script>

<nav class="flex max-w-[10rem] flex-col space-y-4 p-4 items-center">
	<ul class="list-none">
		<li>
			<a href={base} class="flex flex-col items-center space-y-2">
				<img src={logo} alt="Logo" title="Home" class="h-10 w-10" />
				<span>RAM Disk</span>
			</a>
		</li>
		<li aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
			<a href="{base}/" class="flex flex-col items-center space-y-2">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
					class="h-10 w-10"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1h3a1 1 0 100-2h-3a1 1 0 011-1z"
					/>
				</svg>
				<span>Home</span>
			</a>
		</li>
		<li aria-current={$page.url.pathname === '/about' ? 'page' : undefined}>
			<a href="{base}/about" class="flex flex-col items-center space-y-2">
				<svg
					xmlns="http://www.w3.org/2000/svg"
					fill="none"
					viewBox="0 0 24 24"
					stroke="currentColor"
					class="h-10 w-10"
				>
					<path
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M12 6v6m0 0v6m0-6h6m-6 0H6"
					/>
				</svg>
				<span>About</span>
			</a>
		</li>
		<li>
			<a
				href="https://github.com/jonesrussell"
				target="_blank"
				rel="noopener"
				class="flex flex-col items-center space-y-2"
			>
				<img src={github} alt="GitHub" class="h-10 w-10" />
				<span>GitHub</span>
			</a>
		</li>
	</ul>
</nav>
