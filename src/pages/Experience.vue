<script setup lang="ts">
import { ref } from 'vue';
import { useRoute } from "vue-router";
const route = useRoute();
const itemId = route.query.id;
const experiences = ref([
  {
    company: '神通資訊科技股份有限公司',
    position: 'Back-End Software Engineer',
    period: '2022/08 - 2024/08',
    responsibilities: [
      'Developed and maintained the Land Bank of Taiwan website using ZK, SpringMVC and MSSQL.',
      'Collaborated with back-end developers to complete customer\'s requirement.',
      'Wrote system document.'
    ]
  },
  {
    company: '神謀資訊科技有限公司',
    position: 'Contract Software Engineer',
    period: '2024/08 - Present',
    responsibilities: [
        '...'
      // 'Designed and deployed scalable back-end services using Node.js.',
      // 'Created and maintained database schemas using MongoDB.',
      // 'Worked with a team of developers on an Agile development process.'
    ]
  }
]);
</script>

<template>
  <section class="experience-container">
    <h2>Experience</h2>
    <div v-for="experience in experiences" :key="experience.company" class="experience-item">
      <h3>{{ experience.position }} - {{ experience.company }}</h3>
      <p class="work-period">{{ experience.period }}</p>
      <ul class="responsibilities">
        <li v-for="(item, index) in experience.responsibilities" :key="index">
          {{ item }}
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.experience-container {
  padding: 20px 0;
  border-bottom: 1px solid #eee;
}

h2 {
  font-size: 1.8em;
  color: #2c3e50;
  margin-bottom: 20px;
}

.experience-item {
  margin-bottom: 20px;
}

h3 {
  font-size: 1.2em;
  color: #34495e;
  margin-bottom: 5px;
}

.work-period {
  color: #666;
  font-style: italic;
  margin-bottom: 10px;
}

.responsibilities {
  list-style-type: disc;
  padding-left: 20px;
  margin: 0;
  text-align: left;
}

.responsibilities li {
  color: #333;
  margin-bottom: 5px;
  list-style-type: none;
}
</style>
