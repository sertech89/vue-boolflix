<template>
  <header>
      <div class="logo">BOOLFLIX</div>
      <div class="search-area">
          <input type="text" placeholder="Cerca film"
                v-model="searchText"
                @keyup.enter="$emit('search', searchText)"
          />
          <button type="submit" @click="$emit('search', searchText)">Cerca</button>
      </div>
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
    }
</style>