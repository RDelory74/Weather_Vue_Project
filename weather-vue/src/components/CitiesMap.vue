<template>
    <div style="height:300px; width:400px">
      <p>Voici la carte des villes</p>
      <l-map :useGlobalLeaflet="false">
        <l-tile-layer
          
        ></l-tile-layer>
        <l-geo-json :geojson="geojson" :options="geojsonOptions" />
      </l-map>
    </div>
  </template>
  
  <script>
  import "leaflet/dist/leaflet.css";
  import { LMap, LGeoJson, LTileLayer } from "@vue-leaflet/vue-leaflet";
  import { circleMarker } from "leaflet"; // Importer directement circleMarker
  
  export default {
    components: {
      LMap,
      LGeoJson,
      LTileLayer
    },
    data() {
      return {
        geojson: {
          type: "FeatureCollection",
          features: [
            {
              type: "Feature",
              properties: { name: "Ville 1" },
              geometry: {
                type: "Point",
                coordinates: [2.3522, 48.8566] // Coordonnées pour Paris par exemple
              }
            },
            {
              type: "Feature",
              properties: { name: "Ville 2" },
              geometry: {
                type: "Point",
                coordinates: [4.8357, 45.764] // Coordonnées pour Lyon par exemple
              }
            }
          ]
        },
        geojsonOptions: {
          pointToLayer: (feature, latLng) =>
            circleMarker(latLng, { radius: 8 }) // Utiliser circleMarker directement ici
        }
      };
    }
  };
  </script>