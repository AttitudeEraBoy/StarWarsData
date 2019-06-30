<template>
  <div>
    <h1>{{ msg }}</h1>
    <div v-for="peep in people" :key="peep" id="chars">
      <h1>Name : {{peep.name}}</h1>
      <h2>Height : {{peep.height}}</h2>
      <h2>Mass : {{peep.mass}}</h2>
      <h2>Hair color : {{peep.hair_color}}</h2>
      <h2>Skin color : {{peep.skin_color}}</h2>
      <h2>Eye color : {{peep.eye_color}}</h2>
      <h2>Birth year : {{peep.birth_year}}</h2>
      <h2>Gender : {{peep.gender}}</h2>
      <h2>Homeworld : {{peep.homeworld}}</h2>
      <h2>Films : {{peep.films.join(", ")}}</h2>
      <h2>Species : {{peep.species}}</h2>
      <h2>Vehicles : {{peep.vehicles.join(", ")}}</h2>
      <h2>Starships : {{peep.starships.join(", ")}}</h2>
      <h5>Created : {{peep.created}}</h5>
      <h5>Edited : {{peep.edited}}</h5>
      <h5>Url : <a v-bind:href="peep.url">{{peep.url}}</a></h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Informations',
  data(){
    return{
      msg:"Characters",
      people:[]
    }
  },
  created(){
        this.$http.get('https://swapi.co/api/people/').then(function(data){
        this.people = data.body.results;
        this.people.forEach(el => {
          this.$http.get(el.homeworld).then(function(data){
            el.homeworld = data.body.name;
          })
           this.$http.get(el.species.join()).then(function(dat){
           el.species = dat.body.name;
          })

          var i = 0;
          for(i = 0; i < el.films.length; i++){
          this.$http.get(el.films[i]).then(function(dat){
          el.films.push(dat.body.title);
          el.films.shift();
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
  padding:20px;
margin:20px 0;
    box-sizing:border-box;
    border: 3px;
    background-color:grey;
    color: white;
}
</style>
