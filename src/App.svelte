<script>
  import { onMount } from 'svelte'
  import Home from './lib/pages/Home.svelte'
  import Bookshelf from './lib/pages/Bookshelf.svelte'
  import Movies from './lib/pages/Movies.svelte'
  import Albums from './lib/pages/Albums.svelte'
  import Manga from './lib/pages/Manga.svelte'

  const ROUTES = {
    home: { label: 'Home', component: Home },
    books: { label: 'Bookshelf', component: Bookshelf },
    movies: { label: 'Movies', component: Movies },
    albums: { label: 'Albums', component: Albums },
    manga: { label: 'Manga', component: Manga }
  }

  const routeKeys = Object.keys(ROUTES)

  const parseHash = () => {
    if (typeof window === 'undefined') return 'home'
    const raw = window.location.hash.replace(/^#/, '').replace(/^\//, '')
    return routeKeys.includes(raw) ? raw : 'home'
  }

  let activeRoute = 'home'

  const updateRoute = () => {
    activeRoute = parseHash()
  }

  onMount(() => {
    updateRoute()
    window.addEventListener('hashchange', updateRoute)
    return () => window.removeEventListener('hashchange', updateRoute)
  })

  $: ActiveComponent = ROUTES[activeRoute].component
</script>

<div class="layout">
  <header class="site-header">
    <div class="site-brand">
      <div>
        <h1><a href="#/">My Digital Garden</a></h1>
        <p>Simple shelves for books, films, and albums. Add more whenever you like.</p>
      </div>
    </div>
  </header>

  <main class="site-main">
    <svelte:component this={ActiveComponent} />
  </main>

  <nav class="site-nav">
    {#each routeKeys as key}
      <a
        href={key === 'home' ? '#/' : `#/${key}`}
        class:active={activeRoute === key}
        aria-current={activeRoute === key ? 'page' : undefined}
      >
        {ROUTES[key].label}
      </a>
    {/each}
  </nav>

  <footer class="site-footer">
    <small>Data lives in <code>src/data</code>. Tweak those files to grow new views.</small>
  </footer>
</div>
