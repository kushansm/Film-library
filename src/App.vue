<template>
  <div>
    <Header />
    <HeroSection />
    <video-section></video-section>
<!--    <Features />-->
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import HeroSection from './components/HeroSection.vue'
// import Features from './components/Features.vue'
import Footer from './components/Footer.vue'
import VideoSection from "./components/VideoSection.vue";

export default {
  components: {VideoSection, Header, HeroSection, Footer }
}
</script>
