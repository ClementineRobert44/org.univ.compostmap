<template>
    <div class="card">
      <div class="card-image">
        <figure class="image is-4by3">
          <img
            src="https://bulma.io/images/placeholders/1280x960.png"
            alt="Placeholder image"
          />
        </figure>
      </div>
      <div class="card-content">
        <div class="media">
          <div class="media-left">
            <figure class="image is-48x48">
              <img v-bind:src="image" alt="Image compost" />
            </figure>
          </div>
          <div class="media-content">
            <p class="title is-4">Compost {{ id }}</p>
            <p class="subtitle is-6">{{ focusedDay }}</p>
          </div>
        </div>

        <div class="content">
          Horaires d'ouvertures :
          <ul>
            <li
              v-for="horaire in openSchedules"
              v-bind:key="horaire.day"
              v-on:mouseover="getDay(horaire.day)"
            >
              Le {{ horaire.day }} : De {{ horaire.opening_hour }}h à
              {{ horaire.closing_hour }}h
            </li>
          </ul>

          <button class="button is-primary" v-on:click="createNewSchedule">
            Ajouter un jour
          </button>

          <br />

          <a v-bind:href="url + adresse">Adresse: {{ adresse }}</a>
          <br />
          <div v-if="isOpen">Ouvert</div>
          <div v-else>Fermé</div>
        </div>
      </div>
    </div>
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
      openSchedules: [
        { day: "Lundi", opening_hour: 9, closing_hour: 12 },
        { day: "Mardi", opening_hour: 10, closing_hour: 14 },
        { day: "Mercredi", opening_hour: 10, closing_hour: 14 },
        { day: "Jeudi", opening_hour: 10, closing_hour: 14 },
        { day: "Vendredi", opening_hour: 9, closing_hour: 12 },
      ],
      focusedDay: "",
    };
  },
  methods: {
    createNewSchedule() {
      this.openSchedules.push({
        day: "Samedi",
        opening_hour: 9,
        closing_hour: 12,
      });
    },

    deleteLastSchedule() {
      this.openSchedules.pop();
    },

    getDay(day) {
      this.focusedDay = day;
    },
  },
};
</script>
