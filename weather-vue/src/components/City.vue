<template>
    <main>
        <h2>{{ name }}</h2>
        <p>Météo : {{ weather }}</p>
        <p>Température : {{ temperature }}°C</p>
        <p>Dernière mise à jour : {{ new Date(updatedAt).toLocaleString() }}</p>
        <p>Population : {{ population }} Habitants</p>
    </main>
</template>
<script>
import { format, render, cancel, register } from 'timeago.js';

export default {
    name: "MaVille",
    props: {
        cities: {
            type: Object
        },
        population: {
            type: Number
        },
        name: {
            type: String
        },
        weather: {
            type: String
        },
        temperature: {
            type: Number
        },
        updatedAt: {
            type: String
        }
    },
    data() {
        return {
            titreBoutton: "Météo - Liste des villes",
            cities: [
                {
                    name: 'Ville 1',
                    weather: 'Ensoleillé',
                    temperature: 22.0,
                    updatedAt: format(new Date(1544666010224)),
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
<style></style>