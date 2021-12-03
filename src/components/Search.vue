<template>
  <header>
    <div class="searchbar">
      <h1>logonetflix</h1>
      <div id="cerca">
        <input
          type="text"
          placeholder="cerca un film..."
          v-model="searchFilm"
        />
        <button @click.prevent="$emit(`ricercaMovies`, searchFilm)"
        @click.prevent="$emit(`ricercaSeries`, searchSeries)"
        >Cerca</button>
      </div>
    </div>
  </header>
</template>

<script>


export default {
  name: "Search",
  data() {
    return {
      searchFilm: "",
      ricercaSeries: ""
    };
  },
  
    

  
};
</script>

<style scoped lang="scss">
.searchbar {
  height: 100px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: gray;
}
</style>