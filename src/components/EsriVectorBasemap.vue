<script setup>

/*

  ArcGIS Basemap styles:
  https://developers.arcgis.com/documentation/mapping-and-location-services/mapping/basemaps/arcgis-styles/

  Open Basemap styles:
  https://developers.arcgis.com/documentation/mapping-and-location-services/mapping/basemaps/open-styles/

 */

import {vectorBasemapLayer} from 'esri-leaflet-vector'

const props = defineProps(['map'])
const basemapKey = 'arcgis/newspaper'

// Display a style with the Esri Leaflet plugin
vectorBasemapLayer(basemapKey, {
  token: import.meta.env.VITE_ARCGIS_TOKEN
}).addTo(props.map)

</script>

<template>
  <slot/>
</template>

<style scoped>

</style>