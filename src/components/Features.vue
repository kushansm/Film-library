<script setup lang="ts">
</script>

<template>
  <section class="library-section">
    <div class="content">
      <h2>MOVIE LIBRARY</h2>
      <p>
        Lorem ipsum dolor sit amet, consetetur sadipscing elitr,<br />
        sed diam nonumy eirmod tempor invidunt ut labore et<br />
        dolore magna aliquyam erat, sed diam voluptua.
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
  min-height: 60vh;
  padding: 4rem 2rem;
}

.content {
  flex: 1;
}

.empty-side {
  flex: 1;
}
h2 {
  font-size: 2rem;
  margin-bottom: 1rem;
}
p {
  font-size: 1rem;
  line-height: 1.5;
}
</style>
