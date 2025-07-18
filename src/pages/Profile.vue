<script setup lang="ts">
import { computed } from "vue";
import { useRoute } from "vue-router";

// const props = defineProps<{
//   name: string;
//   title: string;
//   email: string;
//   phone: string;
//   github: string;
// }>();
const route = useRoute();
const name = route.query.name;
const title = route.query.title;
const email = route.query.email;
const phone = route.query.phone;
const github = route.query.github as string;

const itemId = route.query.id;

const githubUserName = computed(() => {
  return github.substring(github.lastIndexOf("/") + 1);
})
</script>

<template>
  <v-container fluid class="profile-container">
    <v-row justify="center">
      <v-col cols="12" md="8">
        <h1>{{ name }}</h1>
        <h2>職稱: {{ title }}</h2>
        <div class="contact-info">
          <span>聯絡信箱：{{ email }}</span> |
          <span>手機：{{ phone }}</span> |
          <span>
            GitHub：
            <a :href="github" target="_blank" rel="noopener noreferrer">
              {{ githubUserName }}
            </a>
          </span>
        </div>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
.profile-container {
  text-align: center;
}

.contact-info {
  margin-top: 10px;
  font-size: 0.9em;
  color: #555;
}

.contact-info span {
  margin: 0 10px;
}

h1 {
  margin: 0;
  font-size: 2.5em;
  color: #2c3e50;
}

h2 {
  margin: 5px 0 15px 0;
  font-size: 1.5em;
  font-weight: 300;
  color: #34495e;
}

</style>
