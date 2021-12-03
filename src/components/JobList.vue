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
      <JobListTag v-for="text in getTags" :key="text" :text="text" @tag="manageTags" />
    </div>
  </div>
</template>

<script>
import JobListTag from "./JobListTag.vue";
export default {
  props: ["data"],
  components: { JobListTag },
  data () {
    return {
      selectedTags: [],
      bonjour: null,
    }
  },
  methods: {
    // permet de faie un tableau contenant tous les tags
    manageTags (tag) {
      if (this.selectedTags.every(e => e != tag)) {
        this.selectedTags = [...this.selectedTags, tag];
      }
      else if (this.selectedTags.every(e => e !== tag) == true) {
        this.selectedTags = [...this.selectedTags].splice([...this.selectedTags].indexOf(tag), 1);
        console.log([...this.selectedTags].splice([...this.selectedTags].indexOf(tag), 1));
      }
      this.$emit('tagsList', [...this.selectedTags, tag])
    },
  },
  computed: {
    // Recupère en un seul tableau tous les tags
    getTags () {
      return [this.data.company, this.data.role, this.data.level, ...this.data.languages, ...this.data.tools]
    }
  }
}
</script>

<style>
</style>