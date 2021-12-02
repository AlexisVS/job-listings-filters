<template>
<!-- container -->
  <div class="flex items-center justify-between px-8 py-4 bg-white rounded-md shadow-xl mt-32 mb-9">
    <!-- List Item -->
    <div class="h-full flex items-center space-x-4">
      <!-- Item -->
      <JobFilterTagSearch/>
      <JobFilterTagSearch/>
    </div>
    <span class="underline font-bold text-teal-500 cursor-pointer">Clear</span>
  </div>
</template>

<script>
import JobFilterTagSearch from "./JobFilterTagSearch.vue";
export default {
    components: { JobFilterTagSearch }
}
</script>

<style>
</style>