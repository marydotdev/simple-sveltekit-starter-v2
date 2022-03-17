<script context="module">
  export const prerender = true

  /**
   * @type {import("@sveltejs/kit").Load}
   */
  export const load = async ({ fetch, params }) => {
    let page = 1
    let limit = 10

    if (params.page) {
      try {
        // a url of /posts/page/2 will come through as 'page/2' for params.page
        page = parseInt(params.page.split('page/').pop())
      } catch (e) {
        console.error(e)
      }
    }

    const fetchPostsParams = new URLSearchParams()

    fetchPostsParams.set('page', page)
    fetchPostsParams.set('limit', limit)

    const posts = await fetch(`/posts.json?${fetchPostsParams.toString()}`).then((res) =>
      res.json()
    )

    // if page doesn't exist, direct to page 1
    if (posts.length == 0 && page > 1) {
      return {
        redirect: `/posts`,
        status: 302
      }
    }

    return {
      props: {
        posts,
        page,
        limit
      }
    }
  }
</script>

<script>
  import ArrowLeftIcon from '$lib/components/ArrowLeftIcon.svelte'

  import ButtonLink from '$lib/components/ButtonLink.svelte'

  import PostPreview from '$lib/components/PostPreview.svelte'
  import { name } from '$lib/info.js'

  export let posts
  export let page

  let inputEl;
	function focusSearch(e) {
		if (e.key === '/' && inputEl) inputEl.select();
	}

  let searchTerm = "";

  $: searchTerm

  $: searchedPosts = posts.filter((post) => {
    return post.title.toLowerCase().includes(searchTerm);
  })

  $: isFirstPage = page === 1
  $: hasNextPage = posts[posts.length - 1]?.previous
</script>

<svelte:head>
  <title>{name} | Posts</title>
</svelte:head>

<svelte:window on:keyup={focusSearch} />

<div class="flex flex-col flex-grow">
  <h1 class="!text-5xl sm:!text-7xl !font-bold !mb-8">Posts</h1>

  <input 
  aria-label="Search posts"
  type="text" 
  placeholder="Press / to search" 
  bind:value={searchTerm}
  bind:this={inputEl}
  class="block w-full rounded-md border border-gray-200 bg-white px-4 py-2 text-gray-900 focus:border-blue-500 focus:ring-blue-500 dark:border-gray-900 dark:bg-gray-800 dark:text-gray-100"
   />
  <div class="flex-grow divide-y divide-slate-300 dark:divide-slate-700">
    {#if searchedPosts.length}
      {#each searchedPosts as post}
        <div class="py-8 sm:hover:transform sm:hover:scale-[1.02] sm:transition-all sm:duration-200">
          <PostPreview {post} />
        </div>
      {/each}
      {:else}
      <div class="py-8">
        <p>No results found for '{searchTerm}'.</p>

        <button class="p-2 bg-slate-900/10 text-slate-900 dark:bg-slate-100/10 dark:text-slate-100" on:click={() => (searchTerm = '')}>Clear your search</button>
      </div>
      {/if}
  </div>

  <!-- pagination -->
  <div class="flex visible items-center justify-between pt-8 opacity-70">
    {#if !isFirstPage}
      <ButtonLink raised={false} href={`/posts/page/${page - 1}`}>
        <slot slot="icon-start">
          <ArrowLeftIcon class="h-5 w-5" />
        </slot>
        Previous
        <slot slot="icon-end" /></ButtonLink
      >
    {:else}
      <div />
    {/if}

    {#if hasNextPage}
      <ButtonLink raised={false} href={`/posts/page/${page + 1}`}>Next</ButtonLink>
    {/if}
  </div>
</div>
