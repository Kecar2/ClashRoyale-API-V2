<template>
  <div class="container">
    <div class="row">
      <h1>Clash Royale Cards</h1>

      <input
        type="text"
        class="form-control bg-dark text-light rounded-0 border-0 my-4"
        placeholder="Search Card"
        @keyup="searchCard()"
        v-model="textSearch"
      />

      <table class="table table-dark table-hover">
        <thead>
          <tr>
            <th>{{ loading }}</th>
            <th v-for="title in titles" :key="title">
              {{ title }}
            </th>
          </tr>
        </thead>
        <tbody>
          <Card
            :card="card"
            :index="index"
            v-for="(card, index) in filteredCards"
            :key="card.id"
          />
        </tbody>
      </table>
    </div>
  </div>

  <Card />
</template>

<script>
import Card from "./components/Card.vue";
export default {
  components: { Card },
  name: "App",
  data() {
    return {
      loading: true,
      cards: [],
      filteredCards: [],
      titles: ["#", "Name", "Elixir", "Rarity", "Arena", "Description"],
      textSearch: "",
    };
  },
  mounted() {
    fetch("https://royaleapi.github.io/cr-api-data/json/cards_i18n.json")
      .then((response) => response.json())
      .then((data) => {
        console.log(data);
        this.cards = data;
        this.filteredCards = data;
      })
      .catch((error) => {
        console.log(error);
      });
    // const res = await fetch(
    //   "https://royaleapi.github.io/cr-api-data/json/cards_i18n.json"
    // );
    // const data = await res.json();
    // console.log(data);
    // this.cards = data;
    // this.filteredCards = data;
    // this.loading = false;
  },
  methods: {
    searchCard() {
      this.filteredCards = this.cards.filter((card) =>
        card._lang.name.es.toLowerCase().includes(this.textSearch.toLowerCase())
      );
    },
  },
};
</script>

<style>
</style>
