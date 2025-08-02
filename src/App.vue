<template>
  <div>
    <Header />
    <HeroSection />
    <Movielibrary />
    <video-section />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import HeroSection from './components/HeroSection.vue'
import Movielibrary from './components/Movielibrary.vue';
import Footer from './components/Footer.vue'
import VideoSection from "./components/VideoSection.vue";

export default {
  components: {VideoSection, Header, HeroSection, Footer, Movielibrary }
}
</script>
