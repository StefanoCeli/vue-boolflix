<template>
  <div>
      <ul>
         <li>{{ movie.title }}</li>
         <li 
         v-if= "movie.original_title.toLowerCase() !== movie.title.toLowerCase()"
         >{{ movie.original_title }}</li>
         <li>{{ movie.original_language }}</li>
         <li>{{ movie.vote_average }}</li>
     </ul>
  </div>
</template>

<script>
export default {
    name:'ListMovies',
    props: {
        movie: Object
    }
}
</script>

<style>

</style>