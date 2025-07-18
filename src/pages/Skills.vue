<script setup lang="ts">
import { ref } from 'vue';
import { useRoute } from "vue-router";
const route = useRoute();
const itemId = route.query.id;
const skillCategories = ref([
  {
    category: 'Front-end',
    skills: [
      { name: 'HTML', level: 3 },
      { name: 'CSS', level: 3 },
      { name: 'JavaScript', level: 2 },
      { name: 'TypeScript', level: 2 },
      { name: 'Vue.js', level: 2 },
      { name: 'ZK', level: 2 }
      // { name: 'React', level: 'medium' }
    ]
  },
  {
    category: 'Back-end',
    skills: [
      { name: 'Java', level: 3.5 },
      { name: 'Python', level: 2 },
      { name: 'C', level: 2 },
      { name: 'C++', level: 2 },
      { name: 'C#', level: 2 },
      { name: 'Swift', level: 2 },
      { name: 'Node.js', level: 2 },
      // { name: 'Express.js', level: 'medium' },
      { name: 'Oracle', level: 3 }
    ]
  },
  {
    category: 'Tools and Platforms',
    skills: [
      { name: 'Git', level: 4 },
      { name: 'Docker', level: 2 },
      { name: 'AWS', level: 1 }
    ]
  }
]);
</script>

<template>
  <section class="skills-container">
    <h2>Skills</h2>
    <div v-for="category in skillCategories" :key="category.category" class="skill-category">
      <h3>{{ category.category }}</h3>
      <ul class="skills-list">
        <li v-for="skill in category.skills"
            :key="skill.name"
            class="skill-item">
          <span class="skill-name">{{ skill.name }}</span>
          <div class="star-rating" :style="{'--star-width': (skill.level / 5 * 100) + '%'}">
            <span class="star-ghost">★★★★★</span>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.skills-container {
  --star-width: 0%; /* 可以不加，只是避免IDE靜態分析報錯。 */
  padding: 20px 0;
  border-bottom: 1px solid #eee;
}

h2 {
  font-size: 1.8em;
  color: #2c3e50;
  margin-bottom: 20px;
}

.skill-category {
  /* 每個技能分類之間保留一些底部間距 */
  margin-bottom: 20px;
  text-align: left;
}

h3 {
  font-size: 1.2em;
  color: #34495e;
  margin-bottom: 15px;
  /* 左側的裝飾線 */
  border-left: 4px solid #42b983;
  padding-left: 10px;
}

.skills-list {
  /* 清除 ul 的預設樣式 */
  list-style-type: none;
  padding: 0;
  margin: 0;

  /* 5. 使用 Flexbox 進行佈局 */
  display: flex;
  flex-wrap: wrap; /* 允許項目換行 */
  gap: 10px; /* 設定項目之間的間距 */
}

.skill-item {
  /* 6. 技能標籤的樣式 */
  background-color: #f0f0f0; /* 淺灰色背景 */
  color: #333;
  padding: 8px 15px; /* 上下 8px，左右 15px 的內距 */
  border-radius: 20px; /* 圓角，使其呈現藥丸形狀 */
  font-size: 0.95em;
  font-weight: 500;
  /* 當滑鼠移上去時，顯示手形游標 */
  cursor: default;
  /* 動畫效果，讓滑鼠移上去時有平滑的過渡 */
  transition: all 0.2s ease-in-out;
  /* 這讓星星的絕對定位是相對於這個標籤本身 */
  position: relative;
  /* 讓裡面的元素垂直置中 */
  display: flex;
  align-items: center;
  gap: 8px; /* 名稱和星星之間的間距 */
}

/* 星星評級容器的基礎樣式 */
.star-rating {
  /* 設定寬度和高度，寬度是單顆星星寬度 * 5 */
  /* width: auto; */
  height: 16px;
  /* 讓星星偽元素相對於它定位 */
  position: relative;
  /* 平時隱藏，滑鼠移上去時才顯示 */
  display: none;
  /* 讓 inline-block 元素可以和文字對齊得更好 */
  vertical-align: middle;
}

/* 使用偽元素繪製星星 */
.star-rating::before,
.star-rating::after {
  content: '★★★★★'; /* 五顆星星字符 */
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  font-size: 16px; /* 控制星星大小 */
  line-height: 1;
  letter-spacing: 1px;
}

/* 底層的灰色星星 */
.star-rating::before {
  color: #ddd; /* 未點亮時的顏色 */
  width: 100%; /* 底層灰色星星：寬度永遠是 100% */

}

/* 上層的、根據 level 顯示的金色星星 */
.star-rating::after {
  color: #ffc107; /* 金色 */
  overflow: hidden; /* 隱藏超出寬度的部分 */
  /*
    最關鍵的一步：
    我們使用 CSS 的 calc() 函式來計算寬度。
    `--skill-level` 是我們在 <template> 中綁定的變數。
    (var(--skill-level) / 5) 就是 level 的百分比。
    例如 level 是 3，寬度就是 (3 / 5) * 100% = 60%。
  */
  width: var(--star-width); /* 根據技能等級計算寬度 */
}

.skill-item:hover {
  /* 滑鼠懸停時的樣式 */
  background-color: #42b983; /* 變成主題綠色 */
  color: white;
  transform: translateY(-2px); /* 向上移動一點，產生立體感 */
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.skill-item:hover .skill-name {
  /* 滑鼠懸停時，技能名稱變為白色 */
  color: white;
}

/* 滑鼠懸停時，顯示星星 */
.skill-item:hover .star-rating {
  display: block;
}

.star-ghost {
  visibility: hidden;
  font-size: 16px;
  line-height: 1;
  letter-spacing: 1px;
}

</style>
