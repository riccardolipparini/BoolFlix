<template>
  <main>
      <div class="contain-cards">
          <div class="cards" v-for="films, i in details" :key="i">
            <h1>{{films.title}}</h1>
            <h2>{{films.original_title}}</h2>
            <h3></h3>
            <h4></h4>
          </div>
      </div>
  </main>
</template>

<script>


export default {
  name: 'Cards',

 props:{
    details: Array
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
    height: 800px;
    width: 80%;
    .cards{
        width: calc(100% / 5);
        height: 45%;
        background-color: lightblue
    }
        
}



</style>