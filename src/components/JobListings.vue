
<script setup>
    import JobListing from './JobListing.vue';
    import { ref, defineProps, onMounted } from 'vue';
    import { RouterLink } from 'vue-router';
    import axios from 'axios';
    defineProps({
        limit:Number,
        showButton:{
            type:Boolean,
            default:false
        }
    })
    const jobs = ref([]);

    onMounted(async()=>{
      try{
        const response = await axios.get('/api/jobs');
        jobs.value = response.data;
      }catch(error){
        console.error('Error Fetching Jobs',error);
      }
    })
</script>

<template>
    <section class="bg-green-50 px-4 py-10">
      <div class="container-xl lg:container m-auto">
        <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
          Browse Jobs
        </h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <JobListing v-for="job in jobs.slice(0,limit || jobs.length)" :key="job.id" :job="job"/>
        </div>
      </div>
    </section>

    <section class="m-auto max-w-lg my-10 px-6" v-if="showButton">
      <RouterLink
        to="/jobs"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
        >View All Jobs</RouterLink
      >
    </section>
</template>
