<template>
    <div>
        <h2 v-if="series.length>0">Series</h2>

        <div id="series-list">
            <CardComp 
                v-for="(element, index) in series" 
                :key="index" 
                title="element.title"
                :originalTitle="element.originalTitle"
                :language="element.language"
                :vote="element.vote"
                :poster="element.poster"
                :overview= element.overview
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
    #series-list {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 20px;
    }

    h2 {
        margin: 30px 0;
    }
</style>