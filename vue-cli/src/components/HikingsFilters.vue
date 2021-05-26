<template>
  <section>
    <h2>Ma randonnée personnalisée</h2>
    <section>
      <h3 v-on:click="showFilter1 = !showFilter1">Par durée, distance et difficulté</h3>
      <section v-show="showFilter1">
        <div>
          <label for="duration">Durée de ma randonnée : </label>
          <input id="duration" type="number" v-model="duration" /> h
          <button v-on:click="resetDuration">Reset</button>
        </div>
        <div>
          <label for="distance">Nombre de kilomètres de ma randonnée : </label>
          <input id="distance" type="number" v-model="distance" /> km
          <button v-on:click="resetDistance">Reset</button>
        </div>
        <div>
          <label for="difficulty">Difficulté de ma randonnée : </label>
          <select id="difficulty" v-model="difficulty">
            <option value="0">Toutes difficultées</option>
            <option value="facile">Facile</option>
            <option value="difficile">Difficile</option>
            <option value="moyenne">Moyenne</option>
          </select>
        </div>
        <div v-for="item in filteredByAll()" :key="item.name">
          <h3>{{ item.name }}</h3>
          <ul>
            <li>{{ item.duration }}h</li>
            <li>{{ item.distance }}km</li>
            <li>Difficulté : {{ item.difficulty }}</li>
            <li>A visiter durant la randonnée : {{item.interestName}}</li>
          </ul>
        </div>
      </section>
    </section>

    <section>
      <h3 v-on:click="showFilter2 = !showFilter2">Par centres d'intérêts</h3>
      <section v-show="showFilter2">
        <div id="interests">
          <div v-for="item in hikings" :key="item.interest">
            <input type="checkbox" v-bind:id="item.interest" v-bind:value="item.interest" v-model="interests">
            <label v-bind:for="item.interest">{{item.interestName}}</label>
          </div>
        </div>
        <div v-for="item in filteredByInterests()" :key="item[0].name">
          <h3>{{ item[0].name }}</h3>
          <ul>
            <li>{{ item[0].duration }}h</li>
            <li>{{ item[0].distance }}km</li>
            <li>Difficulté : {{ item[0].difficulty }}</li>
            <li>A visiter durant la randonnée : {{item[0].interestName}}</li>
          </ul>
        </div>
      </section>
    </section>
  </section>
</template>

<script>
export default {
  name: 'HikingsFilters',
  props: {
    hikings: Array
  },
  data: function() {
    return {
      duration: '',
      distance: '',
      difficulty: '',
      interest: '',
      interests: [],
      showFilter1: false,
      showFilter2: false,
      test: 'test'
    }
  },
  methods: {
    resetDistance: function(e) {
      e.preventDefault()
      this.distance = ""
    },
    resetDuration: function(e) {
      e.preventDefault()
      this.duration = ""
    },
    getByDifficulty: function(hiking, difficulty) {
      if (!difficulty || difficulty === '0') return hiking
      return hiking.filter(item => item.difficulty === difficulty)
    },
    getByDuration: function(hiking, duration) {
      if (!duration) return hiking
      return hiking.filter(item => item.duration === duration)
    },
    getByDistance: function(hiking, distance) {
      if (!distance) return hiking
      return hiking.filter(item => item.distance === distance)
    },
    getByInterests: function(hiking, interests) {
      let hikingInterests = []
      for (let i in hiking) {
        hikingInterests.push(hiking[i].interest)
      }
      let interest = hikingInterests.filter(item => interests.includes(item))
      let hikings = []
      for (let i = 0; i < interest.length; i++) {
        hikings.push(hiking.filter(item => item.interest === interest[i]))
      }
      return hikings
    },
    filteredByAll: function() {
      return this.getByDifficulty(this.getByDuration(this.getByDistance(this.hikings, this.distance), this.duration), this.difficulty)
    },
    filteredByInterests: function() {
      return this.getByInterests(this.hikings, this.interests)
    },
  }
}
</script>