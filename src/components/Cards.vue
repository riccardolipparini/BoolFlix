<template>
  <main>
      <div class="contain-cards">
          <div class="cards" v-for="films, i in detailsMovies" :key="i">
            <h1>{{films.title}}</h1>
            <h2>{{films.original_title}}</h2>
            <h3>{{films.vote_average}}</h3>
            <h4>{{films.original_language}}</h4>
          </div>
      

       
          <div class="cards" v-for="series, s in detailsSeries" :key="s">
            <h1>{{series.name}}</h1>
            <h2>{{series.original_title}}</h2>
            <h3>{{series.vote_average}}</h3>
            <div class="flag">
                <img v-if="getFlags() !== `notfound`" :src="getFlags(series)" alt="">
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
        }else if(flag.original_language === ``){
            return `https://upload.wikimedia.org/wikipedia/commons/c/ca/Bandiera_italiana_foto.svg`
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