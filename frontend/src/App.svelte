<script lang="ts">
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
  import { Button } from '$lib/components/ui/button'
</script>

<main>
  <div>
    <a href="https://vite.dev" target="_blank" rel="noreferrer">
      <img src={viteLogo} class="h-24 p-6 will-change-[filter] transition-[filter] duration-300 hover:drop-shadow-[0_0_2em_#646cffaa]" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img src={svelteLogo} class="h-24 p-6 will-change-[filter] transition-[filter] duration-300 hover:drop-shadow-[0_0_2em_#ff3e00aa]" alt="Svelte Logo" />
    </a>
  </div>
  <h1>Vite + Svelte + shadcn-svelte</h1>

  <div class="card">
    <Counter />
  </div>

  <div class="card">
    <h2 class="text-2xl mb-4">shadcn-svelte Components Demo</h2>
    <div class="flex gap-4 flex-wrap justify-center mb-4">
      <Button>Default</Button>
      <Button variant="secondary">Secondary</Button>
      <Button variant="destructive">Destructive</Button>
      <Button variant="outline">Outline</Button>
      <Button variant="ghost">Ghost</Button>
      <Button variant="link">Link</Button>
    </div>
    <div class="flex gap-4 flex-wrap justify-center mb-4">
      <Button size="sm">Small</Button>
      <Button size="default">Default</Button>
      <Button size="lg">Large</Button>
      <Button size="icon">🚀</Button>
    </div>
  </div>

  <p>
    Check out <a href="https://github.com/sveltejs/kit#readme" target="_blank" rel="noreferrer">SvelteKit</a>, the official Svelte app framework powered by Vite!
  </p>

  <p class="text-gray-500">
    Click on the Vite and Svelte logos to learn more
  </p>
</main>