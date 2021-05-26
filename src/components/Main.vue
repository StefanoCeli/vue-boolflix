<template>
  <main>

        <h1>Lista Film</h1>
     <ListMovies
      v-for= "movie in movies" :key= "movie.id"
      :movie = movie
      />
        <p v-if= "moviesNotFound"> Non ho trovato nessun film </p>
        <h1>Lista serie tv</h1>
     <ListSeries
      v-for= "serie in series" :key= "serie.id"
      :serie = serie
      />
       <p v-if= "seriesNotFound"> Non ho trovato nessuna serie tv </p>

  </main>
</template>

<script>
import ListMovies from './ListMovies';
import ListSeries from './ListSeries';

export default {
    name:'Main',
    components:{
        ListMovies,
        ListSeries
    },
    props:{
        movies: Array,
        series: Array,
        moviesNotFound: Boolean,
        seriesNotFound: Boolean
    }
}
</script>

<style>

</style>