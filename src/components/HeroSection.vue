<template>
  <section class="hero">
    <video
        autoplay
        muted
        loop
        playsinline
        class="hero-video"
    >
      <source src="../../src/assets/Header Video.mp4" type="video/mp4" />
      Your browser does not support the video tag.
    </video>
  </section>
</template>

<script>
export default {
  name: 'HeroSection'
}
</script>

<style scoped>
.hero {
  top: 0;
  right: 0;
  left: 0;
  width: 100%;
  height: 80vh;
  position: relative;
  overflow: hidden;
}

.hero-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
</style>
