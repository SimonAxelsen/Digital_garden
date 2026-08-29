<script>
  import manga from '../../data/manga.js'
  import '../styles/collection.css'

  const sortedManga = manga.sort((a, b) => a.title.localeCompare(b.title))
</script>

<section class="collection">
  <header class="collection__header">
    <h2>Manga</h2>
    <p>Entries live in <code>src/data/manga.js</code>. Add properties whenever you need them.</p>
  </header>

  <div class="collection__grid">
    {#each sortedManga as item}
      <article class="collection-card">
        <img
          class="collection-card__image"
          src={item.image}
          alt={`Cover art for ${item.title}`}
          loading="lazy"
        />
        <div class="collection-card__body">
          <h3>{item.title}</h3>
          {#if item.author}
            <p class="collection-card__meta">{item.author}</p>
          {/if}

          {#if item.summary}
            <p class="collection-card__description">{item.summary}</p>
          {/if}

          {#if item.status}
            <p class="collection-card__status">Status: {item.status}</p>
          {/if}

          {#if item.year || (item.tags && item.tags.length)}
            <p class="collection-card__tags">
              {#if item.year}<span>{item.year}</span>{/if}
              {#if item.tags && item.tags.length}<span>{item.tags.join(' • ')}</span>{/if}
            </p>
          {/if}
        </div>
      </article>
    {/each}
  </div>
</section>