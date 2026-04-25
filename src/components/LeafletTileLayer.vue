<script setup>
import {TileLayer} from 'leaflet'

const props = defineProps(['map', 'url'])

new TileLayer(props.url, {
  foo: 'bar',
  attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(props.map)

</script>

<template>
  <slot/>
</template>

<style scoped>

</style>