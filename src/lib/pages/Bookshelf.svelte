<script>
  import books from '../../data/books.js'
  import '../styles/collection.css'

  const sortedBooks = books.sort((a, b) => a.title.localeCompare(b.title))
</script>

<section class="collection">
  <header class="collection__header">
    <h2>Bookshelf</h2>
    <p>Entries live in <code>src/data/books.js</code>. Add properties whenever you need them.</p>
  </header>

  <div class="collection__grid">
    {#each sortedBooks as book}
      <article class="collection-card">
        <img
          class="collection-card__image"
          src={book.image}
          alt={`Cover art for ${book.title}`}
          loading="lazy"
        />
        <div class="collection-card__body">
          <h3>{book.title}</h3>
          {#if book.author}
            <p class="collection-card__meta">{book.author}</p>
          {/if}

          {#if book.summary}
            <p class="collection-card__description">{book.summary}</p>
          {/if}

          {#if book.status}
            <p class="collection-card__status">Status: {book.status}</p>
          {/if}

          {#if book.year || (book.tags && book.tags.length)}
            <p class="collection-card__tags">
              {#if book.year}<span>{book.year}</span>{/if}
              {#if book.tags && book.tags.length}<span>{book.tags.join(' • ')}</span>{/if}
            </p>
          {/if}
        </div>
      </article>
    {/each}
  </div>
</section>
