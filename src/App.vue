<template>
  <div id="app">
    <Title class="title" title="Popular TV Shows"></Title>
    
    <div id="lists">
     <Tv v-for="items in entries" v-bind:key="items.id" v-bind:tvobj="items"/> </div>
    </div>
    
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
var num = 4
import Tv from './components/Tv.vue'
import Title from './components/Title.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Title,
    Tv
  },
  data() {
        return {
            entries: []
        
        }
    },
mounted() {
        axios
            .get("https://api.themoviedb.org/3/tv/popular?api_key=877845e23233313e8824cde8f5a78fbc&language=en-US&page=1")
            .then(response => {
                var tv = response.data.results
                for (let index = 0; index < num; index++) {
                    var title = tv[index].name
                    var view = tv[index].overview
                    var img = "https://image.tmdb.org/t/p/w185" + tv[index].poster_path
                    var id  = index
                    this.entries.push({title:title,overview:view,imgsrc:img,id:id})
                }
                console.log(this.entries)
            })
            .catch(function (error) { // fail
                console.log(error);
            });
    },
}
</script>

<style>
*{
    box-sizing: border-box;
}
#lists{
  margin-top: 20px;
  display: grid;
  grid-template-columns: auto auto auto auto;
  /* grid-auto-columns: auto auto; */
}
@media (max-width: 1240px) {
    #lists {
      grid-template-columns: auto auto;
    }
    
  }
  @media (max-width: 660px) {
    #lists {
      grid-template-columns: auto;
      margin-top: 20px;
    }
    
  }
</style>
