<script>
    import { name } from '$lib/info'
    import MobileNav from './MobileNav.svelte';
    import ThemeToggle from './ThemeToggle.svelte';
    
</script>
    
<nav class="flex justify-between items-center px-4 pt-8 pb-8 tracking-wide">
    <h2 class="text-lg md:text-xl">
        <a href="/" class="block font-semibold text-slate-900 dark:text-slate-100">
            {name}
        </a>
    </h2>
    
    <div class="hidden sm:flex items-center gap-4 md:gap-8 font-medium">
        <a href="/" class="text-slate-900/80 dark:text-slate-100/80 hover:text-slate-900 hover:dark:text-slate-100 hover:transform hover:scale-105 transition-all duration-200">Home</a>
        <a href="/about" class="text-slate-900/80 dark:text-slate-100/80 hover:text-slate-900 hover:dark:text-slate-100 hover:transform hover:scale-105 transition-all duration-200">About</a>
        <a href="/posts" class="text-slate-900/80 dark:text-slate-100/80 hover:text-slate-900 hover:dark:text-slate-100 hover:transform hover:scale-105 transition-all duration-200">Posts</a>
        <ThemeToggle />
    </div>

    <MobileNav />
</nav>