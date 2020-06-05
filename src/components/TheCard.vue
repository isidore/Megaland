<template>
  <div class="card">
    <img :src="cardUrl" alt="card" v-on:click="$emit('clicked')"  />
  </div>
</template>

<script>
export default {
  name: "TheCard",
  props: ["cardUrl"],

};
</script>

<style scoped>
.card img {
  position: absolute;
  margin: 0;
  top:50px;
  width: 100%;
}
</style>
