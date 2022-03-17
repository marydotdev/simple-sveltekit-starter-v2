<script context="module">
  export const prerender = true

  export const load = async ({ fetch }) => {
    return {
      props: {
        recentPosts: await fetch('/posts.json?limit=2').then((res) => res.json())
      }
    }
  }
</script>

<script>
  import ButtonLink from '$lib/components/ButtonLink.svelte'
  import PostPreview from '$lib/components/PostPreview.svelte'
  import Typing from '$lib/components/Typing.svelte';
  import { name } from '$lib/info.js'

  export let recentPosts
</script>

<svelte:head>
  <title>{name}</title>
</svelte:head>

<div class="max-w-6xl mx-auto p-8">
  <div class="mt-12 rounded-2xl text-slate-900 dark:text-slate-100">
      <h1 class="text-4xl sm:text-7xl">
          My name is <br />
          <span class="w-fit text-transparent bg-clip-text bg-gradient-to-r from-cyan-500 to-blue-500">Jane Doeveloper.</span><br />
          <Typing />
      </h1>
  </div>
</div>

  <!-- recent posts -->
  <h2 class="flex items-baseline gap-4 !mb-2">
    Recent Posts
    <ButtonLink href="/posts" size="small" raised={false} class="opacity-60">View All</ButtonLink>
  </h2>
  <div class="grid gap-4 grid-cols-1 sm:grid-cols-2">
    {#each recentPosts as post}
      <div class="flex px-6 py-4 rounded-2xl bg-slate-900/10 dark:bg-slate-100/10 sm:hover:transform sm:hover:scale-[1.02] sm:hover:shadow-lg sm:transition-all sm:duration-200">
        <PostPreview {post} small />
      </div>
    {/each}
  </div>

