<script setup>
import {Map, Control} from 'leaflet'
import * as esri from 'esri-leaflet'
import '@/lib/leaflet-map-with-labels.js'
import '@/lib/leaflet-map-with-labels.css'

import {onMounted, useTemplateRef} from 'vue'

import {ref} from 'vue'

window.L = L
window.L.esri = esri

let panel = useTemplateRef('panel')
let model = defineModel()
let map = ref()

const createMap = async () => {

  if (!map.value) {

    // plugin overrides L.map
    // https://github.com/samanbey/leaflet-mapwithlabels
    map = new Map('map', {
      // map = L.mapWithLabels('map', {
      minZoom: 2,
      zoom: 5,
      center: {lat: 39, lng: -100},
      attribution: {
        test: 'https://icons8.com'
      }
    })

    model.value = map

    Control.Panel = L.Control.extend({
      onAdd: function (map) {
        return panel.value
      },

      onRemove: function (map) {
        // Nothing to do here
      }
    })

    L.control.panel = function (opts) {
      return new L.Control.Panel(opts)
    }

    L.control.panel({position: 'topright'}).addTo(map)
  }

}

onMounted(() => {
  createMap()
})

</script>

<template>
  <div id="map">
    <div ref="panel" id="panel" class="leaflet-control">
      <slot name="panel"></slot>
    </div>
  </div>
  <slot></slot>
</template>

<style scoped>
#map {
  width: 100%;
  height: 100%;
}

#panel {
  background: #fff !important;
  width: 500px;
  max-height: 90vw;
  overflow: auto;
}

</style>