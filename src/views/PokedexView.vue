<template>
    <PokedexAPI />
</template>

<script>
// @ is an alias to /src
import PokedexAPI from '@/components/PokedexAPI.vue' //Import the component

export default {
    name: 'PokedexView',
    components: { PokedexAPI }, //Register the component
    data () {
        return {

        }
    }
}
</script>