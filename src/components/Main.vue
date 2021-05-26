<template>
  <main>
      <Search
      @searchMovie= "this.searchMovies"
     />
     <h1>{{ this.query }}</h1>
  </main>
</template>

<script>
import Search from './Search';
import axios from 'axios';

export default {
    name:'Main',
    components:{
        Search
    },
    data(){
        return{
        apiUrl:"https://api.themoviedb.org/3/search/movie",
        apiKey: '4df959eab3283b1ac2c5a67b1e5247b9',
        query:"",
        language:"it-IT",
        movies:[]
        }
    },
    methods:{
        searchMovies(query){
            this.query = query;
            axios.get(this.apiUrl,{
                params:{
                    api_key: this.apiKey,
                    query: this.query,
                    language: this.language
                }
            })
            .then(resp => {
                this.movies = resp.data.results;
                console.log(this.movies);
            })
            .catch(err => {
                console.log(err);
            })
        }
    }
}
</script>

<style>

</style>