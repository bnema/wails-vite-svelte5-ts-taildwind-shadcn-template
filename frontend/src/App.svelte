<script lang="ts">
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
  import { Button } from '$lib/components/ui/button'
  import { Sun, Moon } from '@lucide/svelte'

  let isDark = $state(true)

  function toggleTheme() {
    isDark = !isDark
    document.documentElement.classList.toggle('dark', isDark)
  }
</script>

<main>
  <div class="absolute top-4 right-4">
    <Button variant="outline" size="icon" onclick={toggleTheme}>
      {#if isDark}
        <Sun class="size-5" />
      {:else}
        <Moon class="size-5" />
      {/if}
    </Button>
  </div>

  <div class="flex items-center justify-center gap-4 mb-8">
    <a href="https://vite.dev" target="_blank" rel="noreferrer">
      <img src={viteLogo} class="h-20 p-4 will-change-[filter] transition-[filter] duration-300 hover:drop-shadow-[0_0_2em_#646cffaa]" alt="Vite Logo" />
    </a>
    <span class="text-4xl text-muted-foreground">+</span>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img src={svelteLogo} class="h-20 p-4 will-change-[filter] transition-[filter] duration-300 hover:drop-shadow-[0_0_2em_#ff3e00aa]" alt="Svelte Logo" />
    </a>
  </div>

  <h1 class="text-4xl font-bold mb-4">Wails + Svelte + shadcn</h1>

  <div class="card">
    <Counter />
  </div>

  <div class="card mt-8">
    <h2 class="text-2xl mb-4">shadcn-svelte Components</h2>
    <div class="flex gap-4 flex-wrap justify-center mb-4">
      <Button>Default</Button>
      <Button variant="secondary">Secondary</Button>
      <Button variant="destructive">Destructive</Button>
      <Button variant="outline">Outline</Button>
      <Button variant="ghost">Ghost</Button>
      <Button variant="link">Link</Button>
    </div>
    <div class="flex gap-4 flex-wrap justify-center">
      <Button size="sm">Small</Button>
      <Button size="default">Default</Button>
      <Button size="lg">Large</Button>
      <Button size="icon">🚀</Button>
    </div>
  </div>

  <p class="mt-8 text-muted-foreground">
    Built with <a href="https://wails.io" target="_blank" rel="noreferrer" class="text-primary hover:underline">Wails</a>,
    <a href="https://svelte.dev" target="_blank" rel="noreferrer" class="text-primary hover:underline">Svelte 5</a>, and
    <a href="https://shadcn-svelte.com" target="_blank" rel="noreferrer" class="text-primary hover:underline">shadcn-svelte</a>
  </p>
</main>
