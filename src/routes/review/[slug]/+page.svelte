<script lang="ts">
  import { page } from '$app/stores'
  import { base } from '$app/paths'
  import { onMount } from 'svelte'

  const APP_STORE_URL = 'https://apps.apple.com/us/app/beanheads/id6752735263'
  const FALLBACK_URL = `${base}/`

  const slug = $page.params.slug

  onMount(() => {
    const timer = setTimeout(() => {
      window.location.href = APP_STORE_URL
    }, 2500)

    return () => clearTimeout(timer)
  })
</script>

<svelte:head>
  <title>Review on Beanheads</title>
  <meta name="apple-itunes-app" content="app-id=6752735263, app-argument=beanheads://review/{slug}" />
</svelte:head>

<div class="min-h-screen flex flex-col items-center justify-center px-4 text-center">
  <a href={FALLBACK_URL}>
    <img
      src="{base}/assets/beanheads_wordmark.png"
      alt="Beanheads"
      class="h-10 md:h-12 w-auto mb-8" />
  </a>

  <div class="rounded-2xl border border-blackbean/10 bg-white p-8 md:p-12 max-w-md w-full shadow-sm">
    <h1 class="text-2xl md:text-3xl font-bold text-night">
      View this review
    </h1>
    <p class="mt-4 text-night/70">
      Open this review in the Beanheads app to see the full details.
    </p>

    <div class="mt-8 flex flex-col gap-3">
      <a
        href={APP_STORE_URL}
        class="inline-flex items-center justify-center rounded-md bg-blackbean text-ivory
        px-6 py-3 font-semibold hover:opacity-90 transition-opacity">
        Download Beanheads
      </a>
      <a
        href={FALLBACK_URL}
        class="text-sm underline underline-offset-2 text-night/60 hover:text-blackbean">
        Go to beanheads.social
      </a>
    </div>

    <p class="mt-6 text-xs text-night/40">
      Redirecting to the App Store in a moment…
    </p>
  </div>
</div>
