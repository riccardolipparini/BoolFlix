<template>
  <main>
    <div class="contain-cards">
      <div class="cards" v-for="(films, i) in detailsMovies" :key="i">
        <img :src="getLocandina(films)" alt="" class="locandina" />
        <div class="contain_locandina">
          <h1>{{ films.title }}</h1>
          <h2>{{ films.original_title }}</h2>
          <div class="stars">
            <font-awesome-icon
              icon="star"
              :class="getStars(films) >= 1 ? `active` : ``"
            />
            <font-awesome-icon
              icon="star"
              :class="getStars(films) >= 2 ? `active` : ``"
            />
            <font-awesome-icon
              icon="star"
              :class="getStars(films) >= 3 ? `active` : ``"
            />
            <font-awesome-icon
              icon="star"
              :class="getStars(films) >= 4 ? `active` : ``"
            />
            <font-awesome-icon
              icon="star"
              :class="getStars(films) >= 5 ? `active` : ``"
            />
          </div>
          <div class="flag">
            <img
              v-if="getFlags(films) !== `notfound`"
              :src="getFlags(films)"
              alt=""
              class="bandiere"
            />
            <p v-if="films.original_language === `notfound`">
              {{ films.original_language }}
            </p>
          </div>
        </div>
      </div>


      <div class="cards" v-for="(series, i) in detailsSeries" :key="i">
        <img :src="getLocandina(series)" alt="" class="locandina" />
        <div class="contain_locandina">
        <h1>{{ series.name }}</h1>
        <h2>{{ series.original_title }}</h2>
        <div class="stars">
          <font-awesome-icon
            icon="star"
            :class="getStars(series) >= 1 ? `active` : ``"
          />
          <font-awesome-icon
            icon="star"
            :class="getStars(series) >= 2 ? `active` : ``"
          />
          <font-awesome-icon
            icon="star"
            :class="getStars(series) >= 3 ? `active` : ``"
          />
          <font-awesome-icon
            icon="star"
            :class="getStars(series) >= 4 ? `active` : ``"
          />
          <font-awesome-icon
            icon="star"
            :class="getStars(series) >= 5 ? `active` : ``"
          />
        </div>
        <div class="flag">
          <img
            v-if="getFlags(series) !== `notfound`"
            :src="getFlags(series)"
            alt=""
            class="bandiere"
          />
          <p v-if="series.original_language === `notfound`">
            {{ series.original_language }}
          </p>
        </div>
        </div>
      </div>

    </div>
  </main>
</template>

<script>
export default {
  name: "Cards",

  props: {
    detailsMovies: Array,
    detailsSeries: Array,
  },
  methods: {
    getFlags(flag) {
      if (flag.original_language === `en`) {
        return `https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/280px-Flag_of_the_United_Kingdom_%283-5%29.svg.png`;
      } else if (flag.original_language === `it`) {
        return `https://upload.wikimedia.org/wikipedia/commons/c/ca/Bandiera_italiana_foto.svg`;
      } else if (flag.original_language === `ja`) {
        return `https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Flag_of_Japan.svg/280px-Flag_of_Japan.svg.png`;
      } else {
        return `notfound`;
      }
    },
    getStars(stelle) {
      var star = Math.round(stelle.vote_average / 2);
      return star;
    },
    getLocandina(image) {
      if (image.poster_path !== null) {
        return `https://image.tmdb.org/t/p/w342${image.poster_path}`;
      } else
        return `https://www.google.com/url?sa=i&url=http%3A%2F%2Fwww.cfpcemon.it%2Fmake-in-granda-arriva-al-cfp-e-porta-genuino&psig=AOvVaw3yuCvOLVQWSYIbQrvjW0QX&ust=1639065165013000&source=images&cd=vfe&ved=0CAsQjRxqFwoTCNCv89TH1PQCFQAAAAAdAAAAABAD`;
    },
  },
};
</script>

<style scoped lang="scss">
main {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.contain-cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  height: 800px;
  width: 80%;
  .cards {
    position: relative;
    width: calc(90% / 5);
    background-color: lightgray;
    margin: 10px;
    .bandiere {
      max-width: 40px;
    }
  }
}

.active {
  color: yellow;
}
.locandina {
  max-width: 100%;
  object-fit: cover;
  display: block;
}
.contain_locandina{
  height: 100%;
  width: 100%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  opacity: 0;
  background-color: rgba(0, 0, 0, 0.6);
  
}
.contain_locandina:hover{
  opacity: 1;
}
</style>