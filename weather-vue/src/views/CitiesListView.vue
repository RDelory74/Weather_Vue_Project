<template>
    <main>
        <h1>{{ titreBoutton }}</h1>
        <p v-if="loading">Requête en cours...</p>
        <p v-if="error" style="color: red;">Erreur : {{ error }}</p>
        <ul>
            <li v-for="(city, index) in cities" :key="index">
                <MaVille :name="city.name" :weather="city.weather" :temperature="city.temperature"
                    :updatedAt="city.updatedAt" :population="city.population" />
            </li>
        </ul>

    </main>
</template>
<script>
import axios from "axios"
import MaVille from '../components/City.vue'
export default {

    components: { MaVille },
    data() {
        return {
            titreBoutton: "Météo - Liste des villes",
            cities: [],
            loading: false,
            error: null,
        }
    },
    methods: {
        async fetchUsers() {
            this.loading = true;
            this.error = null;
            try {
                const result = await axios.get("https://randomuser.me/api/?results=10")
                this.cities = result.data.results
                if (result.ok) {
                    throw new Error('Erreur lors de la récupération des données.');
                }
            } catch (err) {
                this.error = err.message;
            } finally {
                this.loading = false;
            }

        }
    },
    async mounted() {
        await this.fetchUsers()
    }
}

</script>
<style scoped>
li {
    list-style: none;
}
</style>

<!-- <MaVille v-for="(city) in cities" :cities="cities" />-->
<!--:population="population" :name="name" :weather="weather" :temperature="temperature" -->
<!--<div><span v-for="item in cart">{{ item }},</span></div-->

<!--     {
                    name: 'Ville 1',
                    weather: 'Ensoleillé',
                    temperature: 22.0,
                    updatedAt: new Date()
                },
                {
                    name: 'Ville 2',
                    weather: 'Peu nuageux',
                    temperature: 19.5,
                    updatedAt: new Date(),
                    population: 80000
                },
                {
                    name: 'Ma ville', // nom de la ville
                    weather: 'Peu nuageux', // descriptif météo 
                    temperature: 20.55, // température en °C
                    updatedAt: new Date(), // date de dernière mise à jour
                    population: 65000
                }-->