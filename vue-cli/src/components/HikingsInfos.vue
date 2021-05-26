<template>
  <section>
    <h2>Les randonnées</h2>
    <p>Nombre de randonnées : {{ totalHiking }}</p>
    <p>Durée totale : {{ totalDuration }}h</p>
    <p>Distance totale : {{ totalDistance }}km</p>
  </section>
</template>

<script>
export default {
  name: 'HikingsInfos',
  props: {
    totalHiking: Number,
    totalDuration: Number,
    totalDistance: Number,
  }
}
</script>