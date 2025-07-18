<script setup lang="ts">
import { useRoute } from "vue-router";
const route = useRoute();
const itemId = route.query.id;
</script>

<template>
  <section class="about-me-container">
    <h2>About me</h2>
    <p>
      啊?
    </p>
  </section>
</template>

<style scoped>

.about-me-container {
  padding: 20px 0;
  border-bottom: 1px solid #eee;
}

h2 {
  font-size: 1.8em;
  color: #2c3e50;
  margin-bottom: 15px;
}

p {
  font-size: 1.1em;
  line-height: 1.6;
  color: #34495e;
  text-align: justify;
}

</style>
