<template>
  <div id="app">
    <div class="wrapper">
      <Seconds :second="time.second" />
      <Minutes :minute="time.minute" />
      <Hours :hour="time.hour" />
      <Month :month="time.month" />
      <Day :day="time.day" :month="time.month" :year="time.year" />
      <Week :week="time.week" />
    </div>
    <p class="year">{{ time.year }}</p>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Seconds from "./components/Seconds.vue";
import Minutes from "./components/Minutes.vue";
import Hours from "./components/Hours.vue";
import Day from "./components/Day.vue";
import Month from "./components/Month.vue";
import Week from "./components/Week.vue";

@Component({
  components: { Seconds, Minutes, Hours, Day, Month, Week }
})
export default class App extends Vue {
  time: { [time: string]: number } = {
    year: 2020,
    month: 0,
    day: 1,
    week: 0,
    hour: 0,
    minute: 0,
    second: 0
  };

  updateTime(): void {
    const currentTime = new Date();
    this.time = {
      year: currentTime.getFullYear(),
      month: currentTime.getMonth(),
      day: currentTime.getDate(),
      week: currentTime.getDay(),
      hour: currentTime.getHours(),
      minute: currentTime.getMinutes(),
      second: currentTime.getSeconds()
    };
  }

  mounted() {
    setInterval(this.updateTime, 1000);
  }
}
</script>

<style lang="scss">
@import "~normalize.css";
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@300;400&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Lato", sans-serif;
  font-size: 62.5%;
  font-weight: 400;
  background-color: #393e46;
  color: #eeeeee;
}

#app {
  width: 100vw;
  height: 100vh;
  display: grid;
  place-items: center;

  .date {
    position: absolute;
    text-align: right;
    font-size: calc(0.5rem + 0.5vmin);
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    transition: transform 0.5s ease, font-size 0.5s ease, opacity 0.5s ease;
    opacity: 0.6;
  }

  .active {
    font-size: calc(1rem + 0.5vmin);
    opacity: 1;
  }

  .year {
    position: absolute;
    top: 2rem;
    left: 2rem;
    font-size: calc(1rem + 2vmin);
  }
}
</style>
