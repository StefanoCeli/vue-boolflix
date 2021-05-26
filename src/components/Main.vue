<template>
  <main>
      <Search
      @searchMovie= "this.queryGen"
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
        apiKey:"4df959eab3283b1ac2c5a67b1e5247b9",
        query:"",
        language:"it-IT"
        }
    },
    methods:{
        queryGen(query){
            this.query = query;
            axios.get(this.apiUrl,{
                params:{
                    apiKey: this.apiKey,
                    query: this.query,
                    language: this.language
                }
            })
            .then(resp => {
                console.log(resp);
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