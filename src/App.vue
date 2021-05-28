<template>
    <div id="app">
      <!-- richiamo evento custom nell'header che scatenerà la funzione searchMovies -->
        <Header
        @searchMovie= "searchMovies"
        :reset = reset
        />

        <h1 
        v-if="check()"
        >La ricerca non ha prodotto risultati</h1>

        <Main v-if="results.movie.length > 0" type="movie" :list= results.movie />
        <Main v-if="results.tv.length > 0" type="tv" :list= results.tv />

    </div>
</template>

<script>
/* import Vue from 'vue' */
import axios from 'axios';
import Header from './components/Header';
import Main from './components/Main'
/* import FlagIcon from 'vue-flag-icon'
Vue.use(FlagIcon); */

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return {
        apiUrl:"https://api.themoviedb.org/3/search/",
        apiKey: '4df959eab3283b1ac2c5a67b1e5247b9',
        results:{
            "movie":[],
            "tv":[]
        },
        searched:false
    }
  },
    methods:{
        //funzione per la condizione del v-if del titolo
        check(){
            return this.searched && this.results.movie.length === 0 && this.results.tv.length === 0
        },
        //funzione per resettare gli array 
        reset(){
            this.results.movie = [];
            this.results.tv = [];
            this.searched=false;
            },
        //funziona che viene scatenata in base al bottone premuto,passo come parametro l'oggetto che viene mandato tramite $emit
        searchMovies(obj){
            this.reset();//resetto in modo che se la ricerca restituisce un errore non rimangono gli elementi precedenti
            if(obj.type === "all"){
                //in caso venga premuto il bottone per carcare entrambi passo manualmente il type,in modo da richiamare entrambe le funzioni
                this.getApi(obj.text, "movie");
                this.getApi(obj.text, "tv");
            }else{
                this.getApi(obj.text, obj.type);
            }
            this.searched=true;
        },
        //funzione per ricavare i dati
        getApi(query, type){
            if(query !== ""){
                axios.get(this.apiUrl+type,{
                    params:{
                        api_key: this.apiKey,
                        query: query,
                        language: "it-IT"
                    }
                })
                .then(res => {
                    this.results[type] = res.data.results;
                })
                .catch(err => {
                    console.log(err);
                })
            }
        }
    }
}
</script>

<style lang="scss">

</style>
