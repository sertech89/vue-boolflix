<template>
  <main>
    <FilmsListComp :films="films"/>
    <SeriesListComp :series="series"/>
  </main>
</template>

<script>
import FilmsListComp from './FilmsListComp.vue'
import SeriesListComp from './SeriesListComp.vue'
export default {
  name: 'MainComp',
  components: {
      FilmsListComp,
      SeriesListComp
  },
  props: ['films', 'series'],
  data() {
      return {
          
      }
  }
}
</script>

<style scoped lang="scss">
    main {
        padding: 30px;
        background-color: rgb(69, 69, 69);
        color: white;
    }
</style>