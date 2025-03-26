<script setup>
  import Navbar from '@/components/Navbar.vue'
  import {RouterView} from 'vue-router'
</script>

<template>
  <header>
    <div class="wrapper">
      <Navbar />
      <RouterView />
    </div>
  </header>


</template>


