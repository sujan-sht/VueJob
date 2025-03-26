<script setup>
  import Hero from '@/components/Hero.vue'
  import HomeCards from '@/components/HomeCards.vue';
  import JobListings from '@/components/JobListings.vue';

</script>

<template>
  <header>
    <div class="wrapper">
      <Hero />
      <HomeCards />
      <JobListings :limit="3" :showButton="true" />
    </div>
  </header>

</template>
