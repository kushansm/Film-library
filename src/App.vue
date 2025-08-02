<template>
  <div>
    <Header />
    <HeroSection />
<!--    <Features />-->
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import HeroSection from './components/HeroSection.vue'
// import Features from './components/Features.vue'
import Footer from './components/Footer.vue'

export default {
  components: { Header, HeroSection, Footer }
}
</script>
