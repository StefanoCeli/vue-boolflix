<template>
    <header>
        
        <!-- barra di ricerca -->
        <div>
            <input type="text"
             v-model.trim= "findMovie"
             placeholder="Ricerca film e serie tv"
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

<style>

</style>