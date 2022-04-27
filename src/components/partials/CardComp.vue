<template>
    <div class="card">
        <img v-if="poster == null" src="../../assets/img/not-found.png" alt="Cover Not Found">
        <img v-else :src="`https://image.tmdb.org/t/p/w342${poster}`" alt="Poster">
        <div class="card-info">
            <h3>{{ title }}</h3>
            <!-- Il titolo originale viene nascosto se è uguale al titolo  -->
            <div v-if="originalTitle != title"><strong>Original title: </strong>{{ originalTitle }}</div>
            <div class="lang">
                <strong>Language: </strong>
                <span v-if="flags.includes(language)">
                    <img class="flag-icon" :src="require(`../../assets/img/${language}.png`)" alt="Language Flag">
                </span>
                <span v-else>
                    <!-- Chiamata all'API nel caso la bandiera non fosse tra quelle nella cartella locale -->
                    <img class="flag-icon" :src="`https://countryflagsapi.com/png/${language}`" alt="Language Flag">
                </span>
            </div>
            <div class="vote">
                <div v-for="(star, index) in Math.ceil(vote / 2)" :key="index"><img :src="icon" class="star-icon"></div>
                <!-- <div v-for="(star, index) in 5 - Math.ceil(vote / 2)" :key="index"><img src="../../assets/icons/star-empty.svg" class="star-icon"></div> -->
                <div v-for="(star, index) in 5 - Math.ceil(vote / 2)" :key="index"><i class="fa-solid fa-star"/></div>

            </div>
            <div v-if="overview.length > 0" class="overview"><strong>Overview:</strong>
                <p v-if="overview.length > 200">{{overview.substring(0, 200) + '...'}}</p>
                <p v-else>{{ overview }}</p>
            </div>
        </div>
    </div>
</template>

<script>
    import icon from "../../assets/icons/star.svg"
    export default {
        name: 'CardComp',
        props: {
            title: String,
            originalTitle: String,
            language: String,
            vote: Number,
            poster: String,
            overview: String
        },
        data() {
            return {
                flags: ['en', 'it', 'fr', 'es', 'de', 'ja', 'ko'],
                icon: icon
            }
        }
    }
</script>

<style scoped lang="scss">
    @import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css";

    .card {
        display: flex;
        flex-basis: calc(100% / 5);
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background-color: black;
        color: white;
        border: 3px solid rgb(158, 0, 0);
        border-radius: 8px;
        position: relative;
    }

    h3 {
        margin-bottom: 15px;
    }

    .lang {
        margin: 10px 0;
    }

    .flag-icon {
        width: 30px;
    }

    .card-info {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100%;
        width: 100%;
        opacity: 0;
        position: absolute;
        padding: 10px;
        text-align: center;
        z-index: 10;
    }

    .card-info:hover {
        opacity: 0.9;
        background-color: black;
        transition: 0.5s;
    }

    img {
        max-width: 100%;
    }

    .vote {
        display: flex;
    }

    .star-icon {
        width: 20px;
    }

    .overview {
        font-size: 14px;
        margin-top: 10px;
    }
</style>