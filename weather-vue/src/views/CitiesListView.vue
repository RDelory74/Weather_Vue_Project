<template>
    <main>
        <h1>{{ titreBoutton }}</h1>
        <ul>
            <li v-for="(city, index) in cities" :key="index">
                <MaVille :name="city.name" :weather="city.weather" :temperature="city.temperature"
                    :updatedAt="city.updatedAt" :population="city.population" />
            </li>
        </ul>

    </main>
</template>
<script>
import MaVille from '../components/City.vue'
import { format, render, cancel, register } from 'timeago.js';
export default {

    components: { MaVille },
    data() {
        return {
            titreBoutton: "Météo - Liste des villes",
            cities: [
                {
                    name: 'Ville 1',
                    weather: 'Ensoleillé',
                    temperature: 22.0,
                    updatedAt: new Date(),
                    population: 65000
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
                }
            ]
        }
    },
}
</script>
<style scoped>
li{
    list-style: none;
}
</style>

        <!-- <MaVille v-for="(city) in cities" :cities="cities" />-->
        <!--:population="population" :name="name" :weather="weather" :temperature="temperature" -->
        <!--<div><span v-for="item in cart">{{ item }},</span></div-->