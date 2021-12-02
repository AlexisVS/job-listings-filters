<template>
  <div
    class="w-full h-28 flex items-center group bg-white rounded-md shadow-xl py-4 my-6 transform hover:-translate-y-2 transition duration-500"
  >
    <!-- Color Line -->
    <div class="w-1.5 h-28 bg-white group-hover:bg-teal-500 rounded-l-md"></div>

      <img :src="data.logo" class="mx-8" alt />
    <div class="w-full flex justify-between items-center">
      <!-- Image profile -->
      <!-- Post -->
      <div class="flex flex-col justify-start">
        <div class="flex text-sm font-bold space-x-3">
          <p class="text-teal-600">{{ data.company }}</p>
          <span class="bg-teal-600 text-white py-1 px-2 rounded-full text-xs uppercase">New!</span>
          <span class="bg-black text-white py-1 px-2 rounded-full text-xs uppercase">Featured</span>
        </div>

        <h2
          class="text-gray-600 hover:text-teal-600 text-lg font-bold tracking-wide mt-2"
        >{{ data.position }}</h2>

        <div class="flex text-gray-400 text-xs mt-2 font-bold">
          {{ data.postedAt }}
          <span class="mx-6">·</span>
          {{ data.contract }}
          <span class="mx-6">·</span>
          {{ data.location }}
        </div>
      </div>
    </div>

    <!-- Tags -->
    <div class="flex items-center space-x-3 mr-10">
      <!-- Tag item -->
      <JobFilterTagList :text="data.role"/>
    </div>

  </div>
</template>

<script>
import JobFilterTagList from "./JobFilterTagList.vue";
export default {
    props: ["data"],
    components: { JobFilterTagList }
}
</script>

<style>
</style>