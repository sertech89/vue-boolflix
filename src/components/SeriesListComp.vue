
   
<template>
    <div>
        <h2>Series</h2>

        <div class="series-list">
            <CardComp
                v-for="(element, index) in series"
                :key="index"
                :title="element.title"
                :originalTitle="element.originalTitle"
                :language="element.language"
                :vote="element.vote"
            />
        </div>
    </div>
</template>

<script>
import CardComp from './partials/CardComp.vue';
export default {
  name: 'SeriesListComp',
  props: ['series'],
  components: {
      CardComp
  }
}
</script>

<style scoped lang="scss">
    .series-list {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
    }
</style>