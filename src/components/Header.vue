<template>
    <header>
        <form>
            <input type="text"
            v-model.trim= "findMovie"
            placeholder="Ricerca film e serie tv"
            >
            <button
            @click.prevent="$emit('searchMovie',findMovie)"
            >Cerca</button>
        </form>
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
    computed:{

    }
}
</script>

<style>

</style>