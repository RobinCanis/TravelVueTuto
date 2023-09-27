<template>
    <div id="nav">
        <router-link id="logo" to="/"> Vue School Travel App</router-link>
        <router-link 
            v-for="destination in destinations" 
            :key="destination.id" 
            :to="{ name: 'destination.show', params: { id: destination.id, slug: destination.slug } }"
            >
            <h2>{{ destination.name }}</h2>
        </router-link>
    </div>
</template>

<style lang="css">
    #nav .vue-school-active-class {
        color: rgba(173, 250, 137, 0.64);
        border-bottom: 2px solid rgba(173, 250, 137, 0.64);
    }
</style>

<script>
import sourceData from '../data.json';
export default {
    data() {
        return {
            destinations: sourceData.destinations
        }
    }
}
</script>