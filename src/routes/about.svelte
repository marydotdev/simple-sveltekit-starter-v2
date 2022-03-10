<script>
    import SocialLinks from "$lib/components/SocialLinks.svelte";
</script>

<div class="flex flex-col flex-grow not-prose text-slate-900 dark:text-slate-100">
    <h1 class="font-bold text-5xl sm:text-7xl pb-8 sm:pb-12">
        About Me
    </h1>

    <div class="flex flex-col sm:flex-row sm:justify-start sm:gap-8">
        <div class="flex-none mx-auto max-h-80 p-4 mb-8 sm:mb-0 rounded-xl bg-slate-900/10 dark:bg-slate-100/10 backdrop-filter backdrop-blur-lg">
            <img src="/janedoeveloper.jpeg" alt="avatar" class="w-48 h-48 rounded-xl object-cover !shadow-none" />
            <SocialLinks />
        </div>
        
        <div class="flex flex-col gap-8">
            <p class="text-2xl sm:text-4xl">My name is Jane Doeveloper. I'm a front-end developer working at a company.</p>
            <p class="text-xl sm:text-2xl opacity-90">I build blazing fast user experiences on the web. Lorem ipsum dolor sit amet consectetur adipisicing elit. Placeat odit dolore libero labore atque. Explicabo corrupti repellat non velit nemo ad dolorum possimus dolore eius, rem illo, eos libero architecto!</p>
        </div>
    </div>
</div>

