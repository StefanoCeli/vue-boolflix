<template>
    
  <div class="flip-card mb-3">
      <div class="flip-card-inner">

        <div class="flip-card-front">
            <img :src="'https://image.tmdb.org/t/p/w342' + card.poster_path" :alt="card.title || card.name">
        </div>

        <div class="flip-card-back">
            <ul class="list-group">

                <li><strong>Titolo:</strong> {{ card.title || card.name }}</li>

                <li><strong>Titolo originale:</strong> {{ card.original_title || card.original_name }}</li>

                <!-- <li><flag :iso= card.original_language /></li> -->
                <li v-if="flagFound()"><strong>Lingua: </strong>
                  <img :src="pathFlag" :alt="card.original_language">
                </li>

                <li v-else><strong>Lingua:</strong> {{ card.original_language.toUpperCase() }}</li>

                <li><strong>Voto: </strong>
                  <i v-for=" (i, index) in star()" :key="index" class="fas fa-star"></i>
                </li>
                
                <li class="line-clamp"><strong>Descrizione:</strong> {{ card.overview }}</li>

            </ul>
        </div>
    </div>
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
        //funzione che divide il voto a metà per poi arrotondarlo per eccesso
          star(){
            return Math.ceil(this.card.vote_average / 2);
          }
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/utilities.scss';
/* classi per ruotare la card */
.flip-card {
  background-color: transparent;
  max-width: 352px;
  height: 513px;
  perspective: 1000px;
  cursor: pointer;
  padding: 0 5px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.6s;
  transform-style: preserve-3d;
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card:hover .flip-card-inner {
  transform: rotatey(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  border: 1px solid #616161;
  border-radius: 10px;
  overflow: hidden;
}

.flip-card-front {
  background-color: #bbb;
  color: black;
  font-size: 20px;
  font-weight: 700;
  text-align: center;
  img{
    height: 100%;
    width: 100%;
  }
}

.flip-card-back {
  background-color: #000;
  color: white;
  transform: rotateY(180deg);
}
/* /classi per ruotare la card */

ul{
    list-style: none;
    padding: 15px;
     li{
         display: inline-block;
         margin-bottom: 15px;
         i{
           color: yellow;
         }
        img{
            width: 30px;
        }
    }
}
@media screen and (max-width:900px){
  .flip-card{
    max-width: 264px;
    height: 385px;
    padding: 0 3px;
  }
  ul{
    padding: 10px;
    li{
      font-size: 14px;
      margin-bottom: 5px;
      img{
        width: 20px;
      }
    }
  }
}
@media screen and (max-width:700px){
  .flip-card{
    max-width: 235px;
    height: 342px;
  }
  ul{
    padding: 5px;
    li{
      margin-bottom: 5px;
    }
  }
}
</style>