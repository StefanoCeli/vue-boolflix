<template>
    <form>
        <input type="text"
        v-model.trim= "findMovie"
        >
        <button
        @click.prevent="$emit('searchMovie',findMovie)"
        >Cerca</button>
    </form>
</template>

<script>
export default {
    name:'Search',
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