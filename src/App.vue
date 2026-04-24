<script setup>
import LeafletMap from '@/components/LeafletMap.vue'
import EsriVectorBasemap from '@/components/EsriVectorBasemap.vue'
import EsriFeatureLayer from '@/components/EsriFeatureLayer.vue'
import EsriHeatFeatureLayer from '@/components/EsriHeatFeatureLayer.vue'
import {ref} from 'vue'

let map = ref()
let url = 'https://koop-provider-quickbase-app.vercel.app/quickbase/rest/services/builderprogram-jhickok/bvy257quq-bvy26afhg/FeatureServer/0?coords_fid=9'

const copyText = () => {
  navigator.clipboard.writeText(url)
}

</script>

<template>
  <LeafletMap v-model="map">
    <div v-if="map !== undefined">
      <EsriVectorBasemap v-bind:map="map"/>
      <EsriFeatureLayer v-bind:map="map" :url="url"/>
      <EsriHeatFeatureLayer v-bind:map="map" :url="url"/>
    </div>
    <template #panel>

      <div class="card">
        <header>

          <div class="row" style="margin-bottom: 0;">

            <div class="col-9 is-vertical-align">
              <h4 class="text-primary ">Demo of Koop Quickbase Provider</h4>
            </div>

            <div class="col-3 is-right">
              <a href="https://github.com/joelhickok/koop-provider-quickbase-for-arcgis">
                <span class="pi pi-github" style="font-size: 28px;"></span>
              </a>
            </div>

          </div>

        </header>

        <p>
          A plugin for <a href="https://koopjs.github.io/">Koop</a> that pulls realtime data from Quickbase tables,
          transforms it to geospatial data,
          and uses Koop's backend to output a Feature Service URL.
        </p>

        <p>
          This URL can be used in apps or tools that
          ingest services using the ArcGIS Feature Layer service specification.
        </p>

        <p>
          The Koop Quickbase Provider URL formulated for this example pulls data from a demo Quickbase
          table I created showing cities where I have lived. The Quickbase data needs a coordinate field, as
          Quickbase is not geospatial by default. In this case, the URL shows the Quickbase field storing the
          coordinates has an id of <kbd>9</kbd>.
        </p>

        <div class="bg-secondary">
          <span class="pi pi-copy pull-right" style="font-size: 22px; cursor: pointer;"
          @click="copyText()"
          />

          <h4>URL used to produce map data:</h4>
          <code>{{ url }}</code>
        </div>

      </div>

    </template>

  </LeafletMap>
</template>

<style scoped>

</style>
