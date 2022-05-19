<template>
  <div class="card" style="width: 18rem" v-if="card">
    <!-- <img src="" class="card-img-top" alt="" /> -->
    <div class="card-body">
      <h5 class="card-title">{{ card._lang.name.es }}</h5>
      <p class="card-text">{{ card._lang.description.es }}</p>
    </div>
    <ul class="list-group list-group-flush">
      <li class="list-group-item">{{ card.elixir }}</li>
      <li class="list-group-item">{{ card.rarity }}</li>
      <li class="list-group-item">{{ card.type }}</li>
    </ul>
    <div class="card-body">
      <a href="#" class="card-link">Card link</a>
      <a href="#" class="card-link">Another link</a>
    </div>
  </div>
</template>

<script>
export default {
  props: ["card", "index", "loading"],
};
</script>

<style>
</style>