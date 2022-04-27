<template>
  <div>
    <HeaderComp @search="searchTitle" />
    <MainComp :films="films" :series="series" />
  </div>
</template>

<script>
  import HeaderComp from './components/HeaderComp.vue';
  import MainComp from './components/MainComp.vue'
  import axios from 'axios';
  export default {
    name: 'App',
    components: {
      HeaderComp,
      MainComp
    },
    data() {
      return {
        apiKey: '480ca1b608920c32ceb1d868578f7cdf',
        searchText: '',
        films: [],
        series: []
      }
    },
    methods: {
      searchTitle(text) {
        this.searchText = text;
        console.log(this.searchText);

        // svuotamento dell'array dei risultati se è già pieno
        if (this.films.length > 0) {
          this.films = [];
        }
        if (this.series.length > 0) {
          this.series = [];
        }

        if (this.searchText != '') {
          // MOVIE
          axios.get(
              `https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${this.searchText}&language=it-IT`
            )
            .then((res) => {
              console.log(res.data.results);

              res.data.results.forEach(element => {
                let movie = {
                  'title': element.title,
                  'originalTitle': element.original_title,
                  'language': element.original_language,
                  'vote': element.vote_average,
                  'poster': element.poster_path,
                  'overview': element.overview
                }
                this.films.push(movie);
              });
              console.log(this.films);
            });
          // TV SERIES
          axios.get(
              `https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${this.searchText}&language=it-IT`)
            .then((res) => {
              console.log('tv series: ', res.data.results);

              res.data.results.forEach(element => {
                let serie = {
                  'title': element.name,
                  'originalTitle': element.original_name,
                  'language': element.original_language,
                  'vote': element.vote_average,
                  'poster': element.poster_path,
                  'overview': element.overview
                }
                this.series.push(serie);
              });
              console.log(this.series);
            });
        }

      }
    }
  }
</script>

<style lang="scss">
  // Reset
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  body {
    font-family: 'Lato', sans-serif;
    background-color: rgb(69, 69, 69);
  }
</style>