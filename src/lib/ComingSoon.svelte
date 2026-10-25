<script lang="ts">
  let { tag, description }: { tag: string; description: string } = $props();
</script>

<section
  class="relative flex min-h-svh items-center justify-center overflow-hidden bg-[#030508] px-4 pt-28 pb-16 text-white"
>
  <div
    class="relative w-full max-w-xl overflow-hidden rounded-2xl border border-[#2b2d36] bg-[#0b0c12]"
  >
    <div class="flex items-center gap-1.5 px-4 pt-3.5 pb-3">
      {#each ['#ff5f57', '#febc2e', '#28c840'] as color (color)}
        <span class="size-2.5 rounded-full" style:background-color={color}></span>
      {/each}
      <div
        class="ms-auto flex items-center gap-2 rounded-lg bg-white py-1 px-5 text-sm font-bold text-[#0a0b10]"
      >
        {tag}
      </div>
    </div>

    <div class="flex flex-col items-center gap-6 border-t border-[#2b2d36] px-6 py-12 text-center">
      <h1 class="text-3xl font-black tracking-wider md:text-5xl">Coming soon</h1>
      <p class="max-w-md text-base text-white/70 md:text-lg">{description}</p>

      <a href="/" class="mt-2 flex rounded border border-[#848484] p-0.5">
        <div
          class="rounded bg-white/90 px-8 py-2 text-sm font-bold text-black uppercase transition-all duration-200 hover:opacity-90"
        >
          Back home
        </div>
      </a>
    </div>
  </div>
</section>
