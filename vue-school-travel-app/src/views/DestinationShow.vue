<template>
    <div>
        <section v-if="destination" class="destination">
            <div>
                <h1>{{destination.name}}</h1>
                <GoBack/>
                <div class="destination-details">
                    <img :src="`/images/${destination.image}`" :alt="destination.name" />
                    <p>{{destination.description}}</p>
                </div>
            </div>
        </section>
        <section class="experiences">
            <h2> Top Experiences in {{ destination.name }}</h2>
            <div class="card">
                <router-link 
                    v-for="experience in destination.experiences"
                    :key="experience.slug"
                    :to="{name: 'experience.show', params: {experienceSlug: experience.slug}}"
                    >
                <ExperienceCard
                    :experience="experience"/>
                </router-link>
            </div>
            <router-view/>
        </section>
    </div>
</template>

<script>
import sourceData from '../data.json'
import ExperienceCard from '../components/ExperienceCard.vue'
import GoBack from '../components/GoBack.vue'
export default {
    // data() {
    //     return {
    //         destination: null
    //     }
    // },
    components: {
    ExperienceCard,
    GoBack,
},

    props: {
        id: {
            type: Number,
            required: true
        }
    },
    
    computed:{
        // destinationId(){
        //     return parseInt(this.$route.params.id);
        // },
        destination(){
            return sourceData.destinations.find(destination => destination.id === this.id)
        }
    },

    // methods: {
    //     async initData(){
    //         const response = await fetch(`https://travel-dummy-api.netlify.app/${this.$route.params.slug}`)
    //         this.destination = await response.json()
    //     }
    // },

    // async created(){
    //         this.initData()
            
    //         }
            
}
</script>