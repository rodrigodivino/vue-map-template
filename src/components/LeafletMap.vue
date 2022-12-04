<script setup lang="ts">
import * as L from "leaflet";
import "leaflet/dist/leaflet.css";
import { onMounted } from "vue";

const emit = defineEmits<{
  (e: "move", event: L.LeafletEvent): void;
  (e: "zoom", event: L.LeafletEvent): void;
}>();

onMounted(() => {
  const map: L.Map = L.map("map").setView([51.505, -0.09], 13);

  L.tileLayer("https://tile.openstreetmap.org/{z}/{x}/{y}.png", {
    maxZoom: 19,
    attribution:
      '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>',
  }).addTo(map);

  map
    .on("move", (event: L.LeafletEvent) => {
      emit("move", event);
    })
    .on("zoom", (event: L.LeafletEvent) => {
      emit("zoom", event);
    });
});
</script>

<template><div id="map"></div></template>

<style scoped>
#map {
  height: 100%;
}
</style>
