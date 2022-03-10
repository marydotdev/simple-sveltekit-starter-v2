<script>
	import { fade, fly } from 'svelte/transition';
	import { quintIn } from 'svelte/easing';
	import ThemeToggle from './ThemeToggle.svelte';
    import MenuIcon from 'heroicons-svelte/solid/MenuIcon.svelte';
    import XIcon from 'heroicons-svelte/solid/XIcon.svelte'

	
	let isOpen = false;
	let isMenuRendered
	$: {
		if (isOpen) {
			setTimeout(() => {
				isMenuRendered = true;
			}, 20);
			
		} else {
			setTimeout(() => {
				isMenuRendered = false;
			}, 300);
		}
	}
</script>

<div class="sm:hidden text-slate-900 dark:text-slate-100">
	<button
		aria-label="Toggle menu"
		type="button"
        class="w-8 h-8"
		on:click={() => (isOpen = !isOpen)}>
		{#if !isOpen}
			<MenuIcon />
		{:else}
			<XIcon />
		{/if}
	</button>

	{#if isOpen}

	<div class="flex flex-col z-50 absolute left-0 px-4 w-full h-screen bg-slate-100 dark:bg-slate-900"
		in:fade="{{delay: 0, duration: 200, opacity: 0}}"
		out:fade="{{delay: 500, duration: 200, opacity: 0}}">
		<ul
			class="flex flex-col justify-center gap-4 py-12 font-medium uppercase"
			class:menuRendered={isMenuRendered}>
			<li
				class="text-slate-900 dark:text-slate-100">
				<a class="flex justify-center items-center gap-4 w-auto py-4 px-2" 
				on:click={() => setTimeout(() => isOpen = false, 200)}
				in:fly="{{delay: 500, duration: 300, x: 0, y: -300, opacity: 0, easing: quintIn}}"
				out:fly="{{delay: 100, duration: 300, x: 0, y: -300, opacity: 0, easing: quintIn}}"
				href="/">
					<span class="text-3xl">Home</span>
				</a>
			</li>
			
			<li
            class="text-slate-900 dark:text-slate-100">
				<a class="flex justify-center items-center gap-4 w-auto py-4 px-2" 
				on:click={() => setTimeout(() => isOpen = false, 200)} 
				in:fly="{{delay: 400, duration: 300, x: 0, y: -300, opacity: 0, easing: quintIn}}"
				out:fly="{{delay: 200, duration: 300, x: 0, y: -300, opacity: 0, easing: quintIn}}"
				href="/about">
					<span class="text-3xl">About</span>
				</a>
			</li>

			<li
            class="text-slate-900 dark:text-slate-100">
				<a class="flex justify-center items-center gap-4 w-auto py-4 px-2" 
				on:click={() => setTimeout(() => isOpen = false, 200)} 
				in:fly="{{delay: 300, duration: 300, x: 0, y: -300, opacity: 0, easing: quintIn}}"
				out:fly="{{delay: 300, duration: 300, x: 0, y: -300, opacity: 0, easing: quintIn}}"
				href="/posts">
					<span class="text-3xl">Posts</span>
				</a>
			</li>

			<li
            class="text-slate-900 dark:text-slate-100">
				<div class="flex justify-center items-center gap-4 w-auto py-4 px-2" 
				on:click={() => setTimeout(() => isOpen = false, 200)} 
				in:fly="{{delay: 100, duration: 300, x: 0, y: -300, opacity: 0, easing: quintIn}}"
				out:fly="{{delay: 500, duration: 300, x: 0, y: -300, opacity: 0, easing: quintIn}}">
				<div class="p-2 rounded-lg bg-zinc-900/10 dark:bg-zinc-100/10">
					<ThemeToggle />
				</div>
			    </div>
			</li>
		</ul>
	</div>
	{/if}
</div>
