<template>
  <v-app id="app">
    <v-navigation-drawer v-model="drawer" app clipped>
      <DarkMode></DarkMode>
    </v-navigation-drawer>

    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon color="#FF5722" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="title">{{ title }}</v-toolbar-title>
    </v-app-bar>

    <FindWeather></FindWeather>
    <v-main>
      <v-row justify="center"></v-row>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "Погода",
      drawer: false
    };
  }
};
</script>

<style>
img {
  width: 50px;
  background: rgb(107, 104, 104);
  border-radius: 30px;
}
</style>
