<template>
  <div>
      <ul>
         <li>{{ card.title || card.name }}</li>
         <li>{{ card.original_title || card.original_name }}</li>
         <li>{{ card.original_language }}</li>
         <li>{{ card.vote_average }}</li>
     </ul>
  </div>
</template>

<script>
export default {
    name:'Card',
    props: {
        card: Object
    }
}
</script>

<style>

</style>