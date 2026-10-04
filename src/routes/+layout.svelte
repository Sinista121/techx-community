<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/favicon.svg';
	import GithubIcon from '~icons/mdi/github';
	import LinkedInIcon from '~icons/mdi/linkedin';
	import WhatsappIcon from '~icons/ic/baseline-whatsapp';
	import InstagramIcon from '~icons/mdi/instagram';
	import BurgerIcon from '~icons/stash/burger-classic';

	import { page } from '$app/state';
	import { onMount } from 'svelte';

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

	let scrolled = $state(false);
	onMount(() => {
		const handleScroll = () => {
			console.log('SCROLLING', scrolled);
			scrolled = window.scrollY > 130;
		};

		window.addEventListener('scroll', handleScroll, { passive: true });
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
<div>
	<div class="pointer-events-none absolute inset-y-0 top-6 right-6 left-6 z-50">
		<div
			class="pointer-events-auto relative transition-all duration-300 flex font-extrabold w-full items-center tracking-wider justify-between rounded-xl px-5 py-1"
		>
			<h1 class="text-2xl md:text-3xl text-white">TECHX³</h1>

			<nav
				class="fixed left-1/2 -translate-x-1/2 z-60 hidden md:flex border {!scrolled
					? 'border-[#1E2027] bg-[#1E2027]/30'
					: 'border-[#383a42] bg-[#1E2027]/80'} backdrop-blur-xs items-center text-xs gap-2 rounded px-3 py-2 text-white uppercase whitespace-nowrap"
			>
				{#each pages as p, i (i)}
					<a
						href={p.url}
						onclick={() => (currentPage = i)}
						class={`${currentPage == i ? 'bg-white text-black' : ''} hover:bg-white hover:text-black rounded py-1.5 px-3 transition-all duration-300`}
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
			class="fixed right-3 bottom-6 flex flex-col items-center gap-5 rounded-xl bg-white/10 p-2 text-xl pointer-events-auto"
		>
			<a
				href="https://github.com/Sinista121/techx-community"
				class="hover:opacity-70 transition-all duration-200"><GithubIcon /></a
			>
			<a class="hover:opacity-70 transition-all duration-200"><LinkedInIcon /></a>
			<a href="" class="hover:opacity-70 transition-all duration-200"><WhatsappIcon /></a>
			<a class="hover:opacity-70 transition-all duration-200"><InstagramIcon /></a>
		</div>
	</div>
	{@render children()}
</div>
