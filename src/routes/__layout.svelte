<script>
  import '../app.css'
  import '../prism.css'
  import 'focus-visible'
  import Header from '$lib/components/Header.svelte'
  import Footer from '$lib/components/Footer.svelte'

</script>

<div class="min-h-screen max-w-4xl mx-auto flex flex-col">
    <Header />

    <main class="prose prose-slate prose-sm sm:prose sm:prose-slate sm:prose-lg sm:max-w-none dark:prose-invert flex flex-col w-full flex-grow py-4 px-4">
      <slot />
    </main>

    <Footer />
</div>
