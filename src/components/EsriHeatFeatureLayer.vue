<script setup>
import 'leaflet.heat'
import {featureLayer} from 'esri-leaflet-heatmap'

const props = defineProps(['map', 'url'])

featureLayer({
  url: props.url,
  radius: 50,
}).addTo(props.map)

</script>

<template>
  <slot/>
</template>
