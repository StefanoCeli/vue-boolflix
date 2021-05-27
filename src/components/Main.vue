<template>
  <main>
    <h1>{{ titles[type] }}</h1>
    <Card
    v-for= "card in list" 
    :key= "card.id"
    :card = card
    />

  </main>
</template>

<script>
import Card from './Card';

export default {
    name:'Main',
    components:{
        Card
    },
    props:{
        type: String,
        list: Array,
    },
    data(){
        return{
            //sfruttando il type inserito nel tag del main andrò a cambiare in modo dinamico il titolo
            titles:{
                'movie': 'Film trovati',
                'tv': 'Serie tv trovate'
            }
        }
    }
}
</script>

<style>

</style>