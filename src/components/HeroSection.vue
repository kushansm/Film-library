<template>
  <section class="hero" dir="rtl" aria-label="Hero section with background video">
    <video
        autoplay
        muted
        loop
        playsinline
        class="hero-video fade-in"
        aria-hidden="true"
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
  direction: rtl; /* RTL support */
}

.hero-video {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: filter 0.4s ease-in-out;
}

/* Hover effect for WCAG and interactivity */
.hero-video:hover {
  filter: brightness(1.1);
}

/* Fade-in animation */
.fade-in {
  animation: fadeIn 1.5s ease-in-out both;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: scale(1.02);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

</style>
