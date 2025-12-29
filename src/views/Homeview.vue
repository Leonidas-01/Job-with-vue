<script setup>
    import Hero from '@/components/Hero.vue'
    import HomeCart from '@/components/HomeCart.vue'
    import JobListing from '@/components/JobListing.vue'
</script>
<template>
   <Hero />
   <HomeCart />
   <JobListing :limit="3" :showButton="true"/>
</template>