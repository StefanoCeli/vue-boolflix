<template>
  <div id="app">
      <!-- richiamo evento custom nell'header che scatenerà la funzione searchMovies -->
      <Header
      @searchMovie= "this.searchMovies"
     />

    <Main 
    :movies= movies
    :series= series
    :moviesNotFound= moviesNotFound
    :seriesNotFound= seriesNotFound
    />

  </div>
</template>

<script>
import axios from 'axios';
import Header from './/components/Header';
import Main from './components/Main'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return {
        apiUrlMovie:"https://api.themoviedb.org/3/search/movie",
        apiUrlTv:"https://api.themoviedb.org/3/search/tv",
        apiKey: '4df959eab3283b1ac2c5a67b1e5247b9',
        query:"",
        language:"it-IT",
        movies:[],
        series:[],
        moviesNotFound: false,
        seriesNotFound: false
    }
  },
    methods:{
        //funzione per ricercare i film
        searchMovies(query){
            this.query = query;
            axios.get(this.apiUrlMovie,{
                params:{
                    api_key: this.apiKey,
                    query: this.query,
                    language: this.language
                }
            })
            .then(resp => {
                this.movies = resp.data.results;
                if(this.movies.length < 1) this.moviesNotFound = true //se la ricerca non trova nulla restituisce il valore a true
                this.searchSeries(); //all'interno della risposta richiamo la funzione per ricercare le serie tv

            })
            .catch(err => {
                console.log(err);
            })
        },
        //funzione per ricercare le serie tv
        searchSeries(){
            axios.get(this.apiUrlTv,{
                params:{
                    api_key: this.apiKey,
                    query: this.query,
                    language: this.language
                }
            })
            .then(resp =>{
                this.series = resp.data.results;
                if(this.series.length < 1) this.seriesNotFound = true//se la ricerca non trova nulla restituisce il valore a true
               
            })
            .catch(err => {
                console.log(err);
            })    
        }
    }
}
</script>

<style lang="scss">

</style>
