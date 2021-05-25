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
  data: function() {
    return {
      hiking: [
        { name: 'Puyloubier', duration: '1', distance: '3', difficulty: 'difficile', interestName: 'Chapelle Saint-Ser', interest:'1'},
        { name: 'Le tholonet', duration: '3', distance: '9', difficulty: 'moyenne', interestName: 'Barrages Zola et Bimont', interest:'2'},
        { name: 'Vauvenargues', duration: '4', distance: '12', difficulty: 'difficile', interestName: 'Prieuré et Croix de Provence', interest:'3'},
        { name: 'Jouques', duration: '3', distance: '8', difficulty: 'facile', interestName: 'Chapelle Notre-Dame de Consolation', interest:'4'}
      ],
    };
  },
  computed: {
    totalHiking: function() {
      let total = 0;
      for (let item in this.hiking) {
        total = parseInt(item) + 1;
      }
      return total;
    },
    totalDuration: function() {
      let total = 0;
      for (let item in this.hiking) {
        total += parseInt(this.hiking[item].duration);
      }
      return total;
    },
    totalDistance: function() {
      let total = 0;
      for (let item in this.hiking) {
        total += parseInt(this.hiking[item].distance);
      }
      return total;
    },
  },
}
</script>