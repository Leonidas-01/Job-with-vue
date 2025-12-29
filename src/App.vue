<script setup>
  import Navbar from '@/components/Navbar.vue'
  import Hero from '@/components/Hero.vue'
  import HomeCart from '@/components/HomeCart.vue'
  import JobListing from '@/components/JobListing.vue'
</script>
<template>
   <Navbar />
   <Hero />
   <HomeCart />
   <JobListing :limit="3" :showButton="true"/>
</template>