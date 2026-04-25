# koop-quickbase-demo

Leaflet-based map built to demo the [Koop Quickbase Provider](https://github.com/joelhickok/koop-provider-quickbase-for-arcgis).

The app uses Esri Leaflet to consume a Feature Service URL published using Koop and the Quickbase Provider.

Data is pulled from Quickbase and an ETL process produces it as a Feature Service that can be consumed in real-time
using ArcGIS and other products that consume these GeoServices.

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```
