<script>
    import { browser } from '$app/env';
    import MoonIcon from 'heroicons-svelte/solid/MoonIcon.svelte'
    import SunIcon from 'heroicons-svelte/solid/SunIcon.svelte'
  
    let prefersLight = browser ? Boolean(JSON.parse(localStorage.getItem('prefersLight'))) : false
</script>
  
  
  {#if browser}
        <button
          type="button"
          role="switch"
          aria-label="Toggle Dark Mode"
          aria-checked={!prefersLight}
          class="h-8 w-8 p-1"
          on:click={() => {
            prefersLight = !prefersLight
            localStorage.setItem('prefersLight', prefersLight.toString())
  
            if (prefersLight) {
              document.querySelector('html').classList.remove('dark')
            } else {
              document.querySelector('html').classList.add('dark')
            }
          }}
        >
          {#if prefersLight}
          <MoonIcon class="text-slate-900 sm:text-slate-900/80 sm:hover:text-slate-900 hover:transform hover:scale-105 transition-all duration-200" />
          {:else}
          <SunIcon class="text-slate-100 sm:text-slate-100/80 sm:hover:text-slate-100 hover:transform hover:scale-105 transition-all duration-200" />
          {/if}
        </button>
      {/if}