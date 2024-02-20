<script setup>
import Nav from '@/components/NavComponent.vue'
import Hero from '@/views/HeroView.vue'
import About from '@/views/AboutView.vue'
import Music from '@/views/MusicView.vue'
import Service from '@/views/ServicesView.vue'
import Gallery from '@/views/GalleryView.vue'
import Contact from '@/views/ContactView.vue'
import Footer from '@/components/FooterComponent.vue'
</script>

<template>
  <Nav/>

  <section class="main_container" id="Hero">
    <Hero/>
  </section>
  
  <section class="main_container" id="About">
    <About/>
  </section>

  <section class="main_container" id="Music">
    <Music/>
  </section>

  <section class="main_container" id="Services">
    <Service/>
  </section>

  <section class="main_container" id="Gallery">
    <Gallery/>
  </section>

  <section class="main_container" id="Contact">
    <Contact/>
  </section>
    
  <Footer/>

</template>


