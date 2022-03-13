<template>
    <PokemonMap />
</template>

<script>
// @ is an alias to /src
import PokemonMap from '@/components/PokemonMap.vue' //Import the component

export default {
    name: 'MapView',
    components: { PokemonMap }, //Register the component
    data () {
        return {

        }
    }
}
</script>