<template>
  <main>
    
    <div class="container">
        <h1>{{ titles[type] }}</h1>
        <div class="row justify-content-between">
            <Card
            v-for= "card in list" 
            :key= "card.id"
            :card = card
            />
        </div>
    </div>

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