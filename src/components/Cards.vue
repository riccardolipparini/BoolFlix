<template>
  <main>
      <div class="contain-cards">
          <div class="cards" v-for="films, i in detailsMovies" :key="i">
            <h1>{{films.title}}</h1>
            <h2>{{films.original_title}}</h2>
            <h3>{{films.vote_average}}</h3>
            <div class="flag">
                <img v-if="getFlags(films) !== `notfound`" :src="getFlags(films)" alt="">
                <p v-if="films.original_language === `notfound`">{{films.original_language}}</p>
            </div>
          </div>
      
          <div class="cards" v-for="series, i  in detailsSeries" :key="i">
            <h1>{{series.name}}</h1>
            <h2>{{series.original_title}}</h2>
            <h3>{{series.vote_average}}</h3>
            <div class="flag">
                <img v-if="getFlags(series) !== `notfound`" :src="getFlags(series)" alt="">
                <p v-if="series.original_language === `notfound`">{{series.original_language}}</p>
            </div>
          </div>
       </div>
  </main>
</template>

<script>


export default {
  name: 'Cards',

 props:{
    detailsMovies: Array,
    detailsSeries: Array
},
methods:{
    getFlags(flag){
        if(flag.original_language === `en`){
            return `https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Flag_of_the_United_Kingdom_%283-5%29.svg/280px-Flag_of_the_United_Kingdom_%283-5%29.svg.png`
        }else if(flag.original_language === `it`){
            return `https://upload.wikimedia.org/wikipedia/commons/c/ca/Bandiera_italiana_foto.svg`
        }else if(flag.original_language === `ja`){
            return `https://upload.wikimedia.org/wikipedia/commons/thumb/9/9e/Flag_of_Japan.svg/280px-Flag_of_Japan.svg.png`
        }else{
            return `notfound`
        }
    }
        
}
}

</script>

<style scoped lang="scss">
main{
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    
}
.contain-cards{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    height: 800px;
    width: 80%;
    .cards{
        width: calc(90% / 5);
        height: 45%;
        background-color: lightgray;
        margin: 10px;
        img{
            max-width: 30px;
        }
    }
        
}



</style>