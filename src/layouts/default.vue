<template>
  <v-main>
    <v-navigation-drawer :width="208">
      <v-list-item title="Resume" subtitle="Evan Lin"></v-list-item>
      <v-divider></v-divider>
      <v-list-item
        link title="基本資料"
        :to="{path: '/profile', query: {
          name: 'Evan Lin',
          title: 'Software Engineer',
          email: 'evan.lin.company@gmail.com',
          phone: '0912252932',
          github: 'https://github.com/Evan000316'
      }}"></v-list-item>
      <v-list-item link title="關於我" to="/aboutMe"></v-list-item>
      <v-list-item link title="技能" to="/skills"></v-list-item>
      <v-list-item link title="專案經歷" to="/experience"></v-list-item>
      <v-list-item link title="學歷" to="/education"></v-list-item>
    </v-navigation-drawer>
    <router-view />
  </v-main>

  <AppFooter />
</template>

<script lang="ts" setup>
  //
</script>
