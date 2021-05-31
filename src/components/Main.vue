<template>
  <main>
    
    <div class=" wrap p-5">
        <h1 class="text-center mb-5">{{ titles[type].toUpperCase() }}</h1>
        <!-- componente slider e all'interno inserisco le card -->
        <VueSlickCarousel v-bind="settings">
            <Card
            v-for= "card in list" 
            :key= "card.id"
            :card = card
            />
        </VueSlickCarousel>
    </div>

  </main>
</template>

<script>
import Card from './Card';
//importo lo slider installato
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
    name:'Main',
    components:{
        Card,
        VueSlickCarousel 
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
            },
            //impostazioni per lo slider
            settings:{
                "centerMode": true,
                "centerPadding": "10%",
                "focusOnSelect": true,
                "infinite": true,
                "slidesToShow": 4,
                "speed": 500,
                "responsive": [
                    {
                    "breakpoint": 1200,
                    "settings": {
                        "slidesToShow": 3,
                    }
                    },
                    {
                    "breakpoint": 950,
                    "settings": {
                        "slidesToShow": 2,
                        "arrows":false
                    }
                    },
                    {
                    "breakpoint": 650,
                    "settings": {
                        "slidesToShow": 1,
                        "centerPadding": "15%",
                        "arrows":false
                    }
                    }
                ]
            }
        }
    }
}
</script>

<style lang="scss" scoped>
.wrap{
    max-width: 1920px;
    margin: 0 auto;
    h1{
        text-shadow: 4px 4px 2px #000;
    }
}

</style>