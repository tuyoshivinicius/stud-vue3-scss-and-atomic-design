<template>
  <div>
    <div class="card_container">      
      <Card />
      <Card />
      <Card />
    </div>
  </div>
</template>



<script>
import Card from "./components/Card.vue";

export default {
  name: "App",
  components: {
    Card: Card,
  },
};
</script>

<style scoped>
.card_container{
  padding:0px 20px;
}
</style>
