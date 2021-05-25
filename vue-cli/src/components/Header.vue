<template>
    <section>
        <h1>{{ title }}</h1>
        <p>Pour plus de renseignement : <a :href="moreInfos.link" target="_blank">{{ moreInfos.title }}</a></p>
    </section>
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