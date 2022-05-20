<template>
  <div class="card d-flex justify-content-evenly" style="width: 15rem" v-if="card">
    <img src="../assets/clash-royale.png" class="card-img-top" alt="" />
    <div class="card-body">
      <h5 class="card-title text-success">{{ card._lang.name.es }}</h5>
      <p class="card-text text-dark">{{ card._lang.description.es }}</p>
    </div>
    <ul class="list-group list-group-flush">
      <li class="list-group-item"><span>Elixir: </span> {{ card.elixir }}</li>
      <li class="list-group-item"><span>Rarity: </span> {{ card.rarity }}</li>
      <li class="list-group-item"><span>Type: </span> {{ card.type }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["card", "index"],
};
</script>

<style scoped>
.card{
  margin-bottom: 10px;

  
}
</style>