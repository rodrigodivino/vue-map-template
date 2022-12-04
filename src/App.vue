<script setup lang="ts">
import LeafletMap from "./components/LeafletMap.vue";

const handleMapMove = (event: L.LeafletEvent) => {
  console.log("move", (event.target as L.Map).getBounds());
};

const handleMapZoom = (event: L.LeafletEvent) => {
  console.log("zoom");
};
</script>

<template>
  <div id="flex-container">
    <header>
      <h1>Header</h1>
    </header>
    <main>
      <LeafletMap @move="handleMapMove" @zoom="handleMapZoom"></LeafletMap>
    </main>
    <footer>Footer</footer>
  </div>
</template>

<style scoped>
#flex-container {
  display: flex;
  flex-direction: column;
  height: 100%;
}

header {
  width: 100%;
  min-height: 50px;
  background-color: aliceblue;
}

footer {
  width: 100%;
  height: 50px;
  background-color: aliceblue;
  font-size: 1em;
}

main {
  width: 100%;
  flex-grow: 1;
  background-color: antiquewhite;
}
</style>
