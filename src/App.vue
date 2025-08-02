<template>
  <div>
    <Header />
    <HeroSection />
    <Movielibrary />
    <video-section />
    <Contactform />
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import HeroSection from './components/HeroSection.vue'
import Movielibrary from './components/Movielibrary.vue';
import Footer from './components/Footer.vue'
import VideoSection from "./components/VideoSection.vue";
import Contactform   from "./components/Contactform.vue";

export default {
  components: {Contactform, VideoSection, Header, HeroSection, Footer, Movielibrary }
}
</script>
