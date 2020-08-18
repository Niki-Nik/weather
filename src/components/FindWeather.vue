<template>
  <v-main>
    <v-container class="fill-height" fluid>
      <v-row justify="center">
        <v-col cols="12" sm="8" md="4">
          <v-card class="elevation-12">
            <v-toolbar color="#FF5722" dark flat>
              <v-toolbar-title>Узнать погоду</v-toolbar-title>
            </v-toolbar>
            <v-card-text>
              <v-text-field
                color="#FF5722"
                v-model="input"
                label="Название города..."
                type="text"
                v-on:keyup.enter="Discover"
              ></v-text-field>
            </v-card-text>
            <v-card-actions>
              <v-spacer>
                <label class="icon"></label>
                <label class="degrees"></label>
                <p class="weat"></p>
              </v-spacer>
              <v-btn color="#FF5722" @click="Discover" dark>Найти</v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-main>
</template>

<script>
export default {
  data() {
    return {
      getWeather: "",
      input: "",
      url: "http://api.openweathermap.org/data/2.5/weather?",
      q: "q=",
      nameCity: "",
      appid: "&appid=70e1ed322b02acbc57d443dd91065f3e"
    };
  },
  methods: {
    Discover() {
      this.nameCity = this.input;
      fetch(this.url + this.q + this.nameCity + this.appid)
        .then(function(resp) {
          return resp.json();
        })
        .then(function(data) {
          console.log(data);
          document.querySelector(".degrees").innerHTML =
            Math.round(data.main.temp - 273) + "&deg;";
          document.querySelector(".weat").textContent =
            data.weather[0]["description"];
          if (data.weather[0]["icon"] === "03d") {
            document.querySelector(".icon").innerHTML =
              ' <img src="https://openweathermap.org/img/wn/03d@2x.png"/>';
          }
          if (data.weather[0]["icon"] === "03n") {
            document.querySelector(".icon").innerHTML =
              ' <img src="https://openweathermap.org/img/wn/03n@2x.png"/>';
          }
          if (data.weather[0]["icon"] === "01d") {
            document.querySelector(".icon").innerHTML =
              ' <img src="https://openweathermap.org/img/wn/01d@2x.png"/>';
          }
          if (data.weather[0]["icon"] === "01n") {
            document.querySelector(".icon").innerHTML =
              ' <img src="https://openweathermap.org/img/wn/01n@2x.png"/>';
          }
          if (data.weather[0]["icon"] === "02d") {
            document.querySelector(".icon").innerHTML =
              ' <img src="https://openweathermap.org/img/wn/02d@2x.png"/>';
          }
          if (data.weather[0]["icon"] === "04d") {
            document.querySelector(".icon").innerHTML =
              ' <img src="https://openweathermap.org/img/wn/04d@2x.png"/>';
          }
          if (data.weather[0]["icon"] === "04n") {
            document.querySelector(".icon").innerHTML =
              ' <img src="https://openweathermap.org/img/wn/04n@2x.png"/>';
          }
          if (data.weather[0]["icon"] === "02n") {
            document.querySelector(".icon").innerHTML =
              ' <img src="https://openweathermap.org/img/wn/02n@2x.png"/>';
          }
        });
      this.input = "";
    }
  }
};
</script>

<style>
</style>
