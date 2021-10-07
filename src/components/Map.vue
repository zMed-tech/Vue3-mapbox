<template>
  <div id="map"></div>
</template>

<script>
import mapboxgl from "mapbox-gl";
import "mapbox-gl/dist/mapbox-gl.css";
import { onMounted } from "vue";

export default {
  name: "Map",
  setup() {
    onMounted(() => {
      mapboxgl.accessToken = "Your Access Token";
      const map = new mapboxgl.Map({
        container: "map",
        style: "mapbox://styles/mapbox/streets-v11",
      });
      map.on("load", () => {
        map.addSource("usa", {
          type: "geojson",
          data: "https://raw.githubusercontent.com/johan/world.geo.json/master/countries/USA.geo.json",
        });
        map.addLayer({
          id: "usa-fill",
          type: "fill",
          source: "usa",
          paint: {
            "fill-color": "red",
          },
        });
        map.on("click", "usa-fill", function (e) {
          new mapboxgl.Popup()
            .setLngLat(e.lngLat)
            .setHTML("Hello World.")
            .addTo(map);
        });
      });
    });

    return {};
  },
};
</script>

<style lang="scss" scoped>
#map {
  height: 80vh;
  width: 100%;
}
</style>
