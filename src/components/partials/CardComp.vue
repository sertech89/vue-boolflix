<template>
    <div class="card">
        <h3>{{ title }}</h3>
        <div><strong>Original title: </strong>{{ originalTitle }}</div>
        <div>
            <strong>Language: </strong>
            <span v-if="flags.includes(language)">
                <img class="flag-icon" :src="require(`../../assets/img/${language}.png`)" alt="Language Flag">
            </span>
            <span v-else>
                <!-- Chiamata all'API nel caso la bandiera non fosse tra quelle nella cartella locale -->
                <img class="flag-icon" :src="`https://countryflagsapi.com/png/${language}`" alt="Language Flag">
            </span>
            </div>
        <div><strong>Vote: </strong>{{ vote }}</div>
    </div>
</template>

<script>
export default {
  name: 'CardComp',
  props: {
      title: String,
      originalTitle: String,
      language: String,
      vote: Number
  },
  data() {
      return {
          flags: ['en', 'it', 'fr', 'es', 'de', 'ja', 'ko']
      }
  }
}
</script>

<style scoped lang="scss">
    .card {
        display: flex;
        flex-basis: calc(100% / 5);
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: black;
        color: white;
        border: 2px solid red;
    }
    .flag-icon {
        width: 30px;
    }
</style>