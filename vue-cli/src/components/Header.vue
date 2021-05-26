<template>
  <header :style="{backgroundImage:'url(images/mountain-5788303_1920.jpg)'}">
    <h1>{{ title }}</h1>
    <p>Pour plus de renseignement : <a :href="moreInfos.link" target="_blank">{{ moreInfos.title }}</a></p>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data: function() {
    return {
      title: 'Randonnées à La Sainte-Victoire',
      moreInfos: {
        title: 'Grand site Sainte-Victoire', 
        link: 'http://www.grandsitesaintevictoire.com/'
      },
    };
  },
  created: function() {
      document.title = 'Randonnées à la Sainte-Victoire'
  }
}
</script>

<style lang="scss">
  header {
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    h1 {
      margin: 0;
      color: white;
      font-size: 60px;
    }
    h1, p, a {
      color: white;
    }
    p, a {
      font-size: 20px;
    }
  }
</style>