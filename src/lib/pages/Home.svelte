<script>
  import './Home.css'
</script>

<section class="home">
  <div class="home__intro">
    <h2>Welcome to the garden</h2>
    <p>A light place to log books, films, and albums. Add new ideas as the garden grows.</p>
  </div>
  <div class="home__grid">
    <a class="home__card" href="#/books">
      <h3>Bookshelf</h3>
      <p>List current reads, stash tags, and record notes in <code>src/data/books.js</code>.</p>
    </a>
    <a class="home__card" href="#/movies">
      <h3>Movies</h3>
      <p>Track films with fields like director, year, or anything else you append.</p>
    </a>
    <a class="home__card" href="#/albums">
      <h3>Albums</h3>
      <p>Track albums with artist, year, or tags in <code>src/data/albums.js</code>.</p>
    </a>
  </div>
</section>
