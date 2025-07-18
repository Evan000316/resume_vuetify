<script setup lang="ts">
import router from "@/router";
const login = () => {
  router.push({
    path: "/profile",
    query: {
      name: "Evan Lin",
      title: "Software Engineer",
      email: "evan.lin.company@gmail.com",
      phone: "0912252932",
      github: "https://github.com/Evan000316"
    }
  })
}
</script>

<template>
  <v-container>
    <v-row class="justify-center">
      <v-col cols="6">
        <v-card>
          <v-card-title class="text-h5">登入</v-card-title>
          <v-card-text>
            <p>請輸入您的帳號和密碼以登入系統。</p>
          </v-card-text>
          <v-text-field
            clearable
            label="帳號"
            prepend-icon="mdi-account-circle"
            variant="outlined"
            type="email"
            placeholder="請輸入email"
            class="custom-spacing"
          ></v-text-field>
          <v-text-field
            clearable
            label="密碼"
            prepend-icon="mdi-lock"
            variant="outlined"
            type="password"
            hint="密碼須包含英文大寫、小寫、數字，並且長度超過10個字"
            class="custom-spacing"
          ></v-text-field>
          <v-card-actions class="justify-end custom-spacing">
            <v-btn color="primary" variant="outlined" @click="login">登入</v-btn>
            <v-btn color="secondary" variant="outlined">註冊</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<style scoped>
.custom-spacing {
  padding-right: 24px;
  padding-left: 24px;
}
</style>
