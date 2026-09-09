<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import GithubIcon from '~icons/mdi/github';
	import LinkedInIcon from '~icons/mdi/linkedin';
	import WhatsappIcon from '~icons/ic/baseline-whatsapp';
	import InstagramIcon from '~icons/mdi/instagram';
	import BurgerIcon from '~icons/stash/burger-classic';

	import { page } from '$app/state';

	let { children } = $props();

	let pages = [
		{
			name: 'Home',
			url: '/'
		},
		{
			name: 'Code Evening',
			url: '/code'
		},
		{
			name: 'Expo',
			url: '/expo'
		}
	];

	let currentPage = $state(pages.findIndex((p) => p.url === page.url.pathname));
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
<div>
	<div class="pointer-events-none fixed inset-y-0 top-6 right-6 left-6 z-50">
		<div
			class="pointer-events-auto flex font-extrabold w-full items-center tracking-wider justify-between rounded-xl bg-[#1E2027]/80 px-5 py-1 backdrop-blur-xs"
		>
			<h1 class="text-2xl md:text-4xl text-white">TECHX</h1>
			<nav
				class="hidden md:flex items-center text-sm gap-4 rounded px-5 py-2 text-white uppercase whitespace-nowrap"
			>
				{#each pages as p, i (i)}
					<a
						href={p.url}
						onclick={() => (currentPage = i)}
						class={`${currentPage == i ? 'bg-white text-black' : ''} rounded py-1.5 px-3`}
					>
						{p.name}
					</a>
				{/each}
			</nav>
			<a href="/expo" class="flex md:hidden cursor-pointer rounded border border-[#848484] p-0.5">
				<div
					class="rounded bg-white/5 px-5 py-2 text-xs font-bold text-white uppercase transition-all hover:bg-white hover:text-black"
				>
					Expo
				</div>
			</a>
			<a href="/#about" class="hidden md:flex cursor-pointer rounded border border-[#848484] p-0.5">
				<div
					class="rounded bg-white/5 px-5 py-2 text-xs font-bold text-white uppercase transition-all hover:bg-white hover:text-black"
				>
					Learn More
				</div>
			</a>
			<a href="" class="flex md:hidden">
				<BurgerIcon />
			</a>
		</div>
		<div
			class="fixed right-12 bottom-6 flex flex-col items-center gap-5 rounded-xl bg-white/10 p-2 text-xl"
		>
			<a href="https://github.com/Sinista121/techx-community"><GithubIcon /></a>
			<a><LinkedInIcon /></a>
			<a href=""><WhatsappIcon /></a>
			<a><InstagramIcon /></a>
		</div>
	</div>
	{@render children()}
</div>
