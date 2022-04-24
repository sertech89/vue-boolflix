<template>
    <div>
        <h2>Films</h2>

        <div class="films-list">
            <CardComp
                v-for="(element, index) in films"
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
  name: 'FilmsListComp',
  components: {
      CardComp
  },
  props: ['films']
}
</script>

<style scoped lang="scss">
    .films-list {
        display: flex;
        flex-wrap: wrap;
        gap: 20px;
    }
</style>