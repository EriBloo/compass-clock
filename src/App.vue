<template>
  <div id="app">
    <div class="wrapper">
      <Seconds :second="time.second" />
      <Minutes :minute="time.minute" />
      <Hours :hour="time.hour" />
      <Month :month="time.month" />
      <Day :day="time.day" :month="time.month" :year="time.year" />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Seconds from "./components/Seconds.vue";
import Minutes from "./components/Minutes.vue";
import Hours from "./components/Hours.vue";
import Day from "./components/Day.vue";
import Month from "./components/Month.vue";

@Component({
  components: { Seconds, Minutes, Hours, Day, Month }
})
export default class App extends Vue {
  time: { [time: string]: number } = {
    year: 2020,
    month: 0,
    day: 1,
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
}
</style>
