<template>
  <h1>Compost {{ id }}</h1>
  <a v-bind:href="url+adresse">Adresse: {{ adresse }}</a>
  <div class="compost-image">
    <img v-bind:src="image" v-on:mouseover="deleteLastSchedule"/>
  </div>

  <div v-if="isOpen">Ouvert</div>
  <div v-else>Fermé</div>

  <ul> 
    <li v-for="horaire in openSchedules" v-bind:key="horaire.day" v-on:mouseover="getDay(horaire.day)">Le {{ horaire.day }} : De {{ horaire.opening_hour }}h à {{ horaire.closing_hour }}h</li>
  </ul>

  <div>{{ focusedDay }}</div>

  <button v-on:click="createNewSchedule">Ajouter un jour</button>

  
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
      ],
      focusedDay: String
    };
  },
  methods: {
    createNewSchedule() {
      this.openSchedules.push({
        day: 'Samedi', opening_hour: 9, closing_hour: 12
      })
    },

    deleteLastSchedule() {
      this.openSchedules.pop();
    },

    getDay(day){
      this.focusedDay = day;
    }
  }
};
</script>
