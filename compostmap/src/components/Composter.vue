<template>
  <h1>Compost {{ id }}</h1>
  <a v-bind:href="url+adresse">Adresse: {{ adresse }}</a>
  <div class="compost-image">
    <img v-bind:src="image" />
  </div>

  <div v-if="isOpen">Ouvert</div>
  <div v-else>Fermé</div>

  <ul> 
    <li v-for="horaire in openSchedules" v-bind:key="horaire.day">Le {{ horaire.day }} : De {{ horaire.opening_hour }}h à {{ horaire.closing_hour }}h</li>
  </ul>

  
</template>

<script>
export default {
  name: "Composter",
  data() {
    return {
      id: 42,
      adresse: "28 rue des plantes en pots",
      image: "./assets/img/compost1.png",
      url: "https://www.google.com/maps/search/",
      isOpen: false,
      openSchedules : [       
        { day: 'Lundi', opening_hour: 9, closing_hour: 12},
        { day: 'Mardi', opening_hour: 10, closing_hour: 14},
        { day: 'Mercredi', opening_hour: 10, closing_hour: 14},
        { day: 'Jeudi', opening_hour: 10, closing_hour: 14},
        { day: 'Vendredi', opening_hour: 9, closing_hour: 12}
      ]
    };
  },
};
</script>
