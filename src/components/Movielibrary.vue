<script>
export default {
  name: 'Movielibrary'
}
</script>

<template>
  <section class="library-section" lang="en" aria-labelledby="movie-library-title">
    <div class="content fade-in">
      <h2 id="movie-library-title" tabindex="0">MOVIE LIBRARY</h2>
      <p>
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
      </p>
    </div>
    <div class="empty-side"></div>
  </section>
</template>

<style scoped>
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.fade-in {
  animation: fadeIn 1.2s ease forwards;
}

.library-section {
  display: flex;
  background-color: #000;
  color: #fff;
  width: 100%;
  padding: 2rem 7vw;
  flex-wrap: wrap;
  box-sizing: border-box;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
  Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  line-height: 1.5;
}

.content {
  flex: 1;
  min-width: 280px;
}

.empty-side {
  flex: 1;
  min-width: 280px;
}

h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
  word-break: break-word;
  cursor: pointer;
  transition: color 0.3s ease, text-decoration 0.3s ease;
  outline-offset: 2px;
}

/* Hover and focus effect on heading */
h2:hover,
h2:focus {
  color: #1e90ff;
  text-decoration: underline;
  outline: none;
}

p {
  font-size: 1.125rem; /* approx 18px for readability */
  line-height: 1.6;
  color: #eee;
}

@media (max-width: 600px) {
  .library-section {
    flex-direction: column;
    padding: 1.5rem 5vw;
  }

  h2 {
    font-size: 1.5rem;
  }

  p {
    font-size: 1rem;
  }

  .empty-side {
    display: none;
  }
}
</style>
