<script >
export default {
  name: 'Movielibrary'
}
</script>

<template>
  <section class="library-section">
    <div class="content">
      <h2>MOVIE LIBRARY</h2>
      <p>
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
      </p>
    </div>
    <div class="empty-side"></div>
  </section>
</template>

<style scoped>
.library-section {
  display: flex;
  background-color: black;
  color: white;
  width: 100%;
  padding: 2rem 7vw;
  flex-wrap: wrap;
  box-sizing: border-box;
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
}

p {
  font-size: 1rem;
  line-height: 1.5;
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
    font-size: 0.95rem;
  }

  .empty-side {
    display: none;
  }
}

</style>
