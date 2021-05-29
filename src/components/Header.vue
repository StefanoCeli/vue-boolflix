<template>
    <header class="d-flex justify-content-between align-items-center ps-sm-4 pe-sm-4 pt-2 pb-2">
        <h1>BOOLFLIX</h1>
        <div class="d-flex">
            <!-- barra di ricerca -->
            <div>
                <input type="text"
                v-model.trim= "findMovie"
                placeholder="Ricerca film e serie tv"
                class="me-3"
                >
            </div>
            <!-- bottoni -->
            <div>
                <button
                @click.prevent="$emit('searchMovie',{text:findMovie, type:'movie'})"
                >Cerca film</button>
            </div>

            <div>
                <button
                @click.prevent="$emit('searchMovie',{text:findMovie, type:'tv'})"
                >Cerca serie tv</button>
            </div>

            <div>
                <button
                @click.prevent="$emit('searchMovie',{text:findMovie, type:'all'})"
                >Cerca tutto</button>
            </div>
            <div>
                <button
                @click.prevent="reset"
                >Reset</button>
            </div>
        </div>

    </header>
</template>

<script>
export default {
    name:'Header',
    data(){
        return {
            findMovie: ""
        }
    },
    props:{
        reset: Function
    }
}
</script>

<style lang="scss" scoped>
header{
    background-color: #000;
    background-image: linear-gradient(#000,#272727);
    h1{
        color: #D10015;
        text-shadow: 3px 3px 3px #000;
    }
    input{
        width: 250px;
    }
}


</style>