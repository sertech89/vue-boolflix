<template>
    <header>
        <div class="logo">BOOLFLIX</div>
        <div class="search-area">
            <input class="text-input" type="text" placeholder="Cerca film" v-model="searchText"
                @keyup.enter="$emit('search', searchText)" />
            <button class="search-btn" type="submit" @click="$emit('search', searchText)">
                <i class="fa-solid fa-magnifying-glass"></i>
            </button> </div>
    </header>
</template>

<script>
    export default {
        name: 'HeaderComp',
        data() {
            return {
                searchText: ''
            }
        }
    }
</script>

<style scoped lang="scss">
    header {
        height: 80px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: black;
        line-height: 80px;
        padding: 0 20px;
    }

    .logo {
        font-size: 24px;
        font-weight: bold;
        color: red;
    }

    .search-area {
        height: 60px;
        line-height: 60px;
    }
    .text-input {
        padding: 0 10px;
    }
    .text-input, .search-btn {
        height: 30px;
    }
    .text-input::placeholder {
        padding: 0 10px;
    }
    .search-btn {
        color: white;
        background-color: red;
        width: 50px;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px;
    }
</style>