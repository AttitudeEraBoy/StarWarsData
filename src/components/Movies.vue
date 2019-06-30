<template>
  <div>
    <h1>{{ msg }}</h1>
    <div v-for="movie in movies" :key="movie" id="chars">
      <h1>Movie Name : {{movie.title}}</h1>
      <h2>Episode ID : {{movie.episode_id}}</h2>
      <h2>Opening Crawl : {{movie.opening_crawl}}</h2>
      <h2>Director : {{movie.director}}</h2>
      <h2>Producer : {{movie.producer}}</h2>
      <h2>Release Date : {{movie.release_date}}</h2>
      <h4>Characters : {{movie.characters.join(", ")}}</h4>
      <h4>Planets : {{movie.planets.join(", ")}}</h4>
      <h4>Species : {{movie.species.join(", ")}}</h4>
      <h4>Vehicles : {{movie.vehicles.join(", ")}}</h4>
      <h4>Starships : {{movie.starships.join(", ")}}</h4>
      <h5>Created : {{movie.created}}</h5>
      <h5>Edited : {{movie.edited}}</h5>
      <h5>Url : <a v-bind:href="movie.url">{{movie.url}}</a></h5>

    </div>
  </div>
</template>

<script>
export default {
  name: 'Informations',
  data(){
    return{
      msg:"Movies",
      movies:[]
    }
  },
  created(){
      this.$http.get('https://swapi.co/api/films').then(function(data){
        console.log(data.body.results);
        this.movies = data.body.results;
        this.movies.forEach(el => {
          var i = 0;
          for(i = 0; i < el.characters.length; i++){
          this.$http.get(el.characters[i]).then(function(dat){
          el.characters.push(dat.body.name);
          el.characters.shift();
          })
          }
          for(i = 0; i < el.species.length; i++){
          this.$http.get(el.species[i]).then(function(dat){
          el.species.push(dat.body.name);
          el.species.shift();
          })
          }
          for(i = 0; i < el.planets.length; i++){
          this.$http.get(el.planets[i]).then(function(dat){
          el.planets.push(dat.body.name);
          el.planets.shift();
          })
          }
          for(i = 0; i < el.vehicles.length; i++){
          this.$http.get(el.vehicles[i]).then(function(dat){
          el.vehicles.push(dat.body.name);
          el.vehicles.shift();
          })
          }
          for(i = 0; i < el.starships.length; i++){
          this.$http.get(el.starships[i]).then(function(dat){
          el.starships.push(dat.body.name);
          el.starships.shift();
          })
          }
        });
      })
      
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#chars{
    padding:15px;
    margin:15px 0;
    box-sizing:border-box;
    border: 3px;
    background-color:grey;
    color: white;
}
</style>
