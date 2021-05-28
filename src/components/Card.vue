<template>

  <div>
      <ul>
         <li>{{ card.title || card.name }}</li>
         <li>{{ card.original_title || card.original_name }}</li>
         <!-- <li><flag :iso= card.original_language /></li> -->
         <li v-if="flagFound()"><img :src="pathFlag" :alt="card.original_language"></li>
         <li v-if="flagNotFound()">The flag {{ card.original_language.toUpperCase() }} is not found </li>
         <li>{{ card.vote_average }}</li>
     </ul>
  </div>

</template>

<script>
export default {
    name:'Card',
    props: {
        card: Object
    },
    data(){
        return{
            countries:["it","en"],
            pathFlag:""
        }
    },
    methods:{
        //funzione per condizione delle flag trovate
        flagFound(){
            if(this.countries.includes(this.card.original_language)){
                this.pathFlag = require("../assets/img/" + this.card.original_language + ".jpg")
            }
            return this.countries.includes(this.card.original_language)
            
        },
        //funzione per condizione delle flag non trovate
        flagNotFound(){
            return !this.countries.includes(this.card.original_language)
        }
    }
}
</script>

<style lang="scss" scoped>
    img{
        width: 30px;
    }
</style>