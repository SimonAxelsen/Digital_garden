<script>
  import movies from '../../data/movies.js'
  import '../styles/collection.css'

  const sortedMovies = movies.sort((a, b) => a.title.localeCompare(b.title))
</script>

<section class="collection collection--movies">
  <header class="collection__header">
    <h2>Movies</h2>
    <p>Update <code>src/data/movies.js</code> to add director, runtime, notes—whatever details you track.</p>
  </header>

  <div class="collection__grid">
    {#each sortedMovies as movie}
      <article class="collection-card">
        <img
          class="collection-card__image"
          src={movie.image}
          alt={`Poster for ${movie.title}`}
          loading="lazy"
        />
        <div class="collection-card__body">
          <h3>{movie.title}</h3>
          {#if movie.director}
            <p class="collection-card__meta">{movie.director}</p>
          {/if}

          {#if movie.year || (movie.tags && movie.tags.length)}
            <p class="collection-card__tags">
              {#if movie.year}<span>{movie.year}</span>{/if}
              {#if movie.tags && movie.tags.length}<span>{movie.tags.join(' • ')}</span>{/if}
            </p>
          {/if}
        </div>
      </article>
    {/each}
  </div>
</section>
