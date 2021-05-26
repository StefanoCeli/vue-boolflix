<template>
  <div>
      <ul>
         <li>{{ serie.name }}</li>
         <li 
         v-if= "serie.original_name.toLowerCase() !== serie.name.toLowerCase()"
         >{{ serie.original_name }}</li>
         <li>{{ serie.original_language }}</li>
         <li>{{ serie.vote_average }}</li>
     </ul>
  </div>
</template>

<script>
export default {
    name:'ListSeries',
    props: {
        serie: Object
    }
}
</script>

<style>

</style>