<script>
  import albums from '../../data/albums.js'
  import '../styles/collection.css'

  const sortedAlbums = albums.sort((a, b) => a.title.localeCompare(b.title))
</script>

<section class="collection collection--albums">
  <header class="collection__header">
    <h2>Albums</h2>
    <p>Update <code>src/data/albums.js</code> to add artist, genre, notes—whatever details you track.</p>
  </header>

  <div class="collection__grid">
    {#each sortedAlbums as album}
      <article class="collection-card">
        <img
          class="collection-card__image"
          src={album.image}
          alt={`Cover art for ${album.title}`}
          loading="lazy"
        />
        <div class="collection-card__body">
          <h3>{album.title}</h3>
          {#if album.artist}
            <p class="collection-card__meta">{album.artist}</p>
          {/if}

          {#if album.year || (album.tags && album.tags.length)}
            <p class="collection-card__tags">
              {#if album.year}<span>{album.year}</span>{/if}
              {#if album.tags && album.tags.length}<span>{album.tags.join(' • ')}</span>{/if}
            </p>
          {/if}
        </div>
      </article>
    {/each}
  </div>
</section>