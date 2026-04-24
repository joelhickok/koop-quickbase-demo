<script setup>
import {featureLayer} from 'esri-leaflet'

const props = defineProps(['map', 'url'])

const layer = featureLayer({
  url: props.url,
  isModern: false,
  fields: ['*'],
  pointToLayer(feature, latlng) {
    return L.circleMarker(latlng, {
      label: feature.properties.name,
      radius: 8,
      color: 'dodgerblue',
      weight: 1,
      fillColor: 'dodgerblue',
      fillOpacity: 0.3,
    })
  },
  onEachFeature(feature, layer) {
    const content = `
        <div style="text-align: center;">
          <b>${feature.properties.name}</b><br/>
          <span style="color: darkgray;">${feature.properties.region}</span>
        </div>
      `
    const link = `
        <a style="text-align: center; display: block;" target="_blank" href="https://${feature.properties.realm}.quickbase.com/nav/app/${feature.properties.appId}/table/${feature.properties.tableId}/action/dr?rid=${feature.properties.record_id}">
          View Record
        </a>
      `

    layer.bindPopup(content + link)
  }
}).addTo(props.map)

</script>

<template>
  <slot/>
</template>

<style scoped>

</style>