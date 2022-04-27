<template>
    <div>
        <h2 v-if="films.length > 0">Films</h2>

        <div id="films-list">
            <CardComp v-for="(element, index) in films" :key="index" :title="element.title"
                :originalTitle="element.originalTitle" :language="element.language" :vote="element.vote"
                :poster="element.poster" :overview=element.overview />
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
    #films-list {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 20px;
    }

    h2 {
        margin: 30px 0;
    }
</style>