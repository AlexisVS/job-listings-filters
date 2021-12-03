<template>
  <div id="app">
    <div class="container">
      <!-- Ajouter props pour tag et creze la logique -->
      <JobFilter :tags="tagsList" /> 
      <JobList v-for="data in datas" :key="data.company" :data="data" @tagsList="dataTagsList" />
    </div>
  </div>
</template>

<script>
  import JobList from './components/JobList.vue';
  import JobFilter from './components/JobFilter.vue';
  import data from '../exo-ressources/data.json';

export default {
    name: "App",
    data () {
      return {
        datas: data,
        selectedTags: [],
        tagsList: [],
      }
    },
    components: { JobFilter, JobList },
    methods: {
      dataTagsList (data) {
        this.tagsList = data;
      }
    }
}
</script>

<style lang="sass" scoped>
#app
  min-height: 100vh
  width: 100%
  margin: 0 auto
  display: flex
  flex-direction: column
  align-items: center
  background-color: #e6fdff
  &::before 
    content: ''
    display: block
    position: absolute
    top: 0
    width: 100%
    height: 155px
    background-image: url('./assets/bg-header-desktop.svg')
    background-color: #4f9497
    background-repeat: none
  .container
    z-index: 10
  
</style>
