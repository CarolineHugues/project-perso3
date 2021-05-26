<template>
  <section>
    <HikingsInfos 
        :totalDistance="totalDistance"
        :totalDuration="totalDuration"
        :totalHiking="totalHiking"
    />
    <HikingsFilters
        :hikings="getHikings"
    />
  </section>
</template>

<script>
import HikingsInfos from './HikingsInfos.vue';
import HikingsFilters from './HikingsFilters.vue';

export default {
  name: 'Hikings',
  components: {
    HikingsInfos,
    HikingsFilters,
  },
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
    getHikings: function() {
        return this.hiking;
    }
  },
}
</script>