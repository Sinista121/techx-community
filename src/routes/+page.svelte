<script lang="ts">
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  import { cubicOut, quintOut } from 'svelte/easing';

  let isIntroActive = $state(false);
  let showText = $state(false);
  let showCube = $state(false);
  let showSlogan = $state(false);

  const cards = [
    {
      id: 'expo',
      tag: '01 / SHOWCASE',
      title: 'Expo',
      href: '/expo',
      text: 'Show off what you have built. Demo your projects, swap feedback and see what everyone else is making.'
    },
    {
      id: 'game-jam',
      tag: '02 / BUILD FAST',
      title: 'Game Jam',
      href: '/game-jam',
      text: 'Team up, pick a theme and make a game in one high-energy sprint. Mistakes are welcome.'
    },
    {
      id: 'code-evening',
      tag: '03 / CASUAL',
      title: 'Code Evening',
      href: '/code-evening',
      text: 'Relaxed evenings to code, fix tricky bugs over pizza and learn from each other.'
    }
  ];

  const whatsapp = "https://chat.whatsapp.com/LIgKW1fDkhI7v8tXpkjhLA";

  const lines = [
    { type: 'comment', text: '// events' },
    { type: 'link', text: 'Expo', href: '/expo', color: '#8ab4ff' },
    { type: 'link', text: 'Game Jam', href: '/game-jam', color: '#8ab4ff' },
    { type: 'link', text: 'Code Evening', href: '/code-evening', color: '#8ab4ff' },
    { type: 'comment', text: '// community' },
    { type: 'link', text: 'About us', href: '/#about', color: '#c4a7ff' },
    { type: 'link', text: 'Join the community', href: '/#about', color: '#c4a7ff' },
    { type: 'link', text: 'Code of conduct', href: '/code-of-conduct', color: '#c4a7ff' }
    // { type: 'comment', text: '// contact' },
    // {
    //   type: 'link',
    //   text: 'hello@techx.example',
    //   href: 'mailto:hello@techx.example',
    //   color: '#7ee0a8'
    // }
  ];

  onMount(() => {
    setTimeout(() => (showText = true), 300);
    setTimeout(() => (showCube = true), 1100);
    setTimeout(() => (showSlogan = true), 1500);
    setTimeout(() => (isIntroActive = false), 2600);
  });
</script>

<svelte:head><title>TechX³</title></svelte:head>

<main>
  {#if isIntroActive}
    <div
      out:fly={{ y: -1000, duration: 800, easing: quintOut }}
      class="fixed inset-0 z-50 flex items-center justify-center bg-[#0a0a0a] px-4"
    >
      <div class="flex flex-wrap items-center justify-center select-none">
        {#if showText}
          <h1
            in:fade={{ duration: 600 }}
            class="text-4xl font-black tracking-wider text-white md:text-5xl"
          >
            TECHX
          </h1>
        {/if}

        {#if showCube}
          <div
            in:fly={{ y: -300, duration: 700, easing: cubicOut }}
            class="relative w-8 h-8 flex items-center justify-center"
          >
            <span class="text-4xl font-black tracking-wider text-white md:text-5xl">³</span>
          </div>
        {/if}

        {#if showSlogan}
          <h1
            in:fade={{ duration: 600 }}
            class="w-full text-center text-xl font-black tracking-wider text-white md:w-auto md:text-4xl"
          >
            <span class="hidden md:inline">- # </span>We Build Tech
          </h1>
        {/if}
      </div>
    </div>
  {/if}

  <section class="relative h-svh min-h-130">
    <img
      srcset="hero-large3.jpg 600w, hero-large3.jpg 1200w, hero-large3.jpg 2000w"
      alt="Crisp background"
      class="absolute h-full w-full object-cover"
    />
    <div class="absolute h-full w-full bg-black/65"></div>

    <div class="absolute inset-0 z-10 flex flex-col p-2 md:p-6">
      <div
        class="flex h-full w-full flex-col items-center justify-center gap-8 px-4 text-center md:gap-10"
      >
        <div class="max-w-4xl">
          <h1 class="title text-3xl font-bold uppercase leading-tight md:text-5xl">
            Welcome to our community
          </h1>
          <p
            class="mx-auto mt-4 max-w-sm text-base font-semibold text-[#ddddde] text-shadow-sm sm:max-w-md md:max-w-none md:text-2xl"
          >
            Where students collaborate, build <br class="hidden md:block" /> and innovate new
            technology
          </p>
        </div>
        <div class="flex flex-wrap justify-center gap-2">
          <a href={whatsapp} target="_blank" class="flex cursor-pointer rounded border border-[#848484] p-0.5">
            <div
              class="rounded bg-white/90 text-black text-sm px-8 py-2 font-bold uppercase transition-all duration-200 hover:opacity-90 md:px-10"
            >
              Join Us
            </div>
          </a>
          <a href="/#about" class="flex cursor-pointer rounded border border-[#848484] p-0.5">
            <div
              class="rounded bg-[#1E2027] text-white text-sm px-8 py-2 font-bold uppercase transition-all duration-200 hover:bg-white/90 hover:text-black md:px-10"
            >
              Explore
            </div>
          </a>
        </div>
      </div>
      <div
        class="pointer-events-none absolute bottom-6 left-2 flex flex-col items-center gap-4 opacity-80 md:left-6 md:gap-10 md:opacity-100"
      >
        <div class="h-6 w-1 bg-white md:h-10"></div>
        <img
          src="tech-vector.svg"
          alt="tech visual"
          class="h-50 w-auto object-contain text-white md:h-60"
        />
      </div>
      <div
        class="pointer-events-none absolute top-24 right-2 flex flex-col items-center gap-3 opacity-80 md:top-20 md:right-6 md:gap-5 md:opacity-100"
      >
        <img
          src="tech-vector.svg"
          alt="tech visual"
          class="h-50 w-auto object-contain text-white md:h-60"
        />
        <div class="h-6 w-1 bg-white md:h-10"></div>
      </div>
    </div>
  </section>
  <section id="about" class="w-full bg-[#090b0f] px-4 py-12 text-center md:px-30 md:py-24">
    <h2 class="mx-auto max-w-4xl text-2xl font-bold leading-tight text-balance md:text-4xl">
      A COMMUNITY PEOPLE COME BACK TO
    </h2>
    <p class="mx-auto mt-3 max-w-2xl text-sm text-white/85 md:text-lg">
      We are a lively tech community where we team up, build cool things and make friends who love
      tech as much as you do.
    </p>

    <div class="mt-10 grid gap-6 text-left md:mt-12 md:grid-cols-3 md:gap-8">
      {#each cards as card (card.id)}
        <a
          href={card.href}
          class="flex flex-col overflow-hidden rounded-3xl border-2 border-[#1F222B] bg-[#0C0E15] text-[#0a0b10] transition-transform duration-200 hover:-translate-y-1.5"
        >
          <div class="overflow-hidden bg-[#030508] pt-4">
            <img alt="" src={`/${card.id}.svg`} class="block h-auto w-full" />
          </div>
          <div class="flex flex-col gap-2.5 px-5 py-4">
            <span class="text-xs font-bold tracking-[0.16em] text-[#6b6e7a]">{card.tag}</span>
            <h3 class="text-xl font-bold text-white">{card.title}</h3>
            <p class="text-sm text-[#88898f]">{card.text}</p>
          </div>
        </a>
      {/each}
    </div>
  </section>
</main>

<footer class="w-full bg-[#030508] px-4 py-12 text-white md:px-30 md:py-20">
  <div class="grid gap-10 md:grid-cols-12 md:gap-10">
    <div class="flex flex-col items-start gap-5 md:col-span-5 md:my-auto md:gap-6">
      <a href="/" class="text-3xl font-black tracking-wider">TECHX³</a>
      <p class="max-w-sm text-sm text-white/70 md:text-base">
        A student tech community where we collaborate, build and innovate new technology together.
      </p>
      <a href={whatsapp} target="_blank" class="cursor-pointer rounded border border-[#848484] p-0.5">
        <div
          class="rounded bg-white/90 px-10 py-2 text-sm font-bold uppercase text-black transition-all duration-200 hover:opacity-90"
        >
          Join Us
        </div>
      </a>
    </div>

    <nav class="overflow-hidden rounded-2xl border border-[#2b2d36] bg-[#0b0c12] md:col-span-7">
      <div class="flex gap-1.5 px-4 pb-3 pt-3.5">
        {#each ['#ff5f57', '#febc2e', '#28c840'] as color (color)}
          <span class="size-2.5 rounded-full" style:background-color={color}></span>
        {/each}
      </div>
      <ol class="flex flex-col gap-2 px-4 pb-4">
        {#each lines as line, n (n)}
          <li class="flex items-center gap-1 text-[13px] leading-5">
            <span class="w-5 shrink-0 text-[11px] text-[#6a6d7a] select-none">{n + 1}</span>
            {#if line.type === 'comment'}
              <span class="font-mono text-[#6a6d7a]">{line.text}</span>
            {:else}
              <a
                href={line.href}
                style:color={line.color}
                class="rounded py-0.5 font-medium transition-opacity duration-200 hover:underline hover:underline-offset-4 focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-white"
              >
                {line.text}
              </a>
            {/if}
          </li>
        {/each}
      </ol>
    </nav>
  </div>

  <div
    class="mt-10 flex flex-col-reverse items-start justify-between gap-5 border-t border-white/10 pt-6 md:mt-14 md:flex-row md:items-center md:gap-6 md:pt-8"
  >
    <p class="text-sm text-white/50">© 2026 TechX³. All rights reserved.</p>

    <div class="flex items-center gap-3">
      <div
        class="flex items-center gap-2 rounded-lg bg-white px-3 py-2 text-sm font-bold text-[#0a0b10] shadow-lg"
      >
        <span class="size-2.5 rounded-full bg-[#0b0c12]"></span>
        Built by TechX
      </div>
    </div>
  </div>
</footer>