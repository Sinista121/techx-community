<script lang="ts">
  import './layout.css';
  import favicon from '$lib/assets/favicon.png';
  import GithubIcon from '~icons/mdi/github';
  //   import LinkedInIcon from '~icons/mdi/linkedin';
  import WhatsappIcon from '~icons/ic/baseline-whatsapp';
  import InstagramIcon from '~icons/mdi/instagram';
  import BurgerIcon from '~icons/stash/burger-classic';
  import CloseIcon from '~icons/mdi/close';

  import { page } from '$app/state';
  import { onMount } from 'svelte';

  import { fly } from 'svelte/transition';
  import { cubicOut } from 'svelte/easing';

  let { children } = $props();

  let pages = [
    { name: 'Home', url: '/' },
    { name: 'Expo', url: '/expo' },
    { name: 'Game Jam', url: '/game-jam' },
    { name: 'Code Evening', url: '/code-evening' }
  ];

  let currentPage = $derived(pages.findIndex((p) => p.url === page.url.pathname));
  let scrolled = $state(false);
  let mounted = $state(false);
  let menuOpen = $derived(false);

  onMount(() => {
    mounted = true;

    const handleScroll = () => {
      scrolled = window.scrollY > 130;
    };

    window.addEventListener('scroll', handleScroll, { passive: true });
    return () => window.removeEventListener('scroll', handleScroll);
  });
</script>

<svelte:head><link rel="icon" href={favicon} /></svelte:head>
<svelte:window onkeydown={(e) => e.key === 'Escape' && (menuOpen = false)} />

<div>
  <div class="pointer-events-none absolute inset-y-0 top-6 right-6 left-6 z-50">
    <div
      class="pointer-events-auto relative transition-all duration-300 flex font-extrabold w-full items-center tracking-wider justify-between rounded-xl px-5 py-1"
    >
      <h1 class="text-2xl md:text-3xl text-white">TECHX³</h1>

      {#if mounted}
        <nav
          in:fly={{ y: -20, duration: 800, easing: cubicOut }}
          class="fixed left-1/2 -translate-x-1/2 z-60 hidden md:flex border {!scrolled
            ? 'border-[#1E2027] bg-[#1E2027]/30'
            : 'border-[#383a42] bg-[#1E2027]/80'} backdrop-blur-xs items-center text-xs gap-2 rounded px-3 py-2 text-white uppercase whitespace-nowrap"
        >
          {#each pages as p, i (i)}
            <a
              href={p.url}
              class={`${currentPage == i ? 'bg-white text-black' : 'border border-[#7d7d7d]'} min-w-20 text-center tracking-wider hover:bg-white hover:text-black rounded py-1.5 px-3 transition-all duration-300 hover:delay-50`}
            >
              {p.name}
            </a>
          {/each}
        </nav>
      {/if}

      <a href="/#about" class="hidden md:flex cursor-pointer rounded border border-[#848484] p-0.5">
        <div
          class="rounded bg-white/5 px-5 py-2 text-xs font-bold text-white uppercase transition-all hover:bg-white hover:text-black"
        >
          Learn More
        </div>
      </a>

      <button
        type="button"
        class="flex cursor-pointer text-3xl text-white md:hidden bg-[#1F222B] rounded p-1"
        aria-label={menuOpen ? 'Close menu' : 'Open menu'}
        aria-expanded={menuOpen}
        aria-controls="mobile-menu"
        onclick={() => (menuOpen = !menuOpen)}
      >
        {#if menuOpen}<CloseIcon />{:else}<BurgerIcon />{/if}
      </button>

      {#if menuOpen}
        <nav
          id="mobile-menu"
          transition:fly={{ y: -12, duration: 250, easing: cubicOut }}
          class="absolute inset-x-0 top-full mt-2 flex flex-col gap-2 rounded-xl border border-[#383a42] bg-[#1E2027]/95 p-3 text-sm uppercase backdrop-blur-md md:hidden"
        >
          {#each pages as p, i (i)}
            <a
              href={p.url}
              onclick={() => (menuOpen = false)}
              class="rounded px-4 py-3 text-center tracking-wider text-white transition-all duration-200 {currentPage ===
              i
                ? 'bg-white text-black'
                : 'border border-[#7d7d7d] hover:bg-white hover:text-black'}"
            >
              {p.name}
            </a>
          {/each}
          <a
            href="/#about"
            onclick={() => (menuOpen = false)}
            class="rounded bg-white/90 px-4 py-3 text-center font-bold tracking-wider text-black"
          >
            Learn More
          </a>
        </nav>
      {/if}
    </div>
    <div
      class="fixed right-3 bottom-6 flex flex-col items-center gap-5 rounded-xl bg-white/10 p-2 text-xl pointer-events-auto"
    >
      <a
        href="https://github.com/Sinista121/techx-community"
        class="hover:opacity-70 transition-all duration-200"><GithubIcon /></a
      >
      <!-- <a class="hover:opacity-70 transition-all duration-200"><LinkedInIcon /></a> -->
      <a
        href="https://chat.whatsapp.com/LIgKW1fDkhI7v8tXpkjhLA"
        class="hover:opacity-70 transition-all duration-200"><WhatsappIcon /></a
      >
      <a
        href="https://www.instagram.com/techx3_mahedubai"
        class="hover:opacity-70 transition-all duration-200"><InstagramIcon /></a
      >
    </div>
  </div>
  {@render children()}
</div>
