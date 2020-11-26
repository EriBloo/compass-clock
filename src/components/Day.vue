<template>
  <div class="days">
    <p
      :class="{ active: n - 1 === day }"
      class="day"
      :style="{
        transform: 'rotate(' + (day - n + 1) * (360 / daysInMonth) + 'deg)'
      }"
      v-for="n in daysInMonth"
      :key="n"
    >
      {{ n - 1 }}
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Seconds extends Vue {
  @Prop(Number) readonly day!: number;
  @Prop(Number) readonly month!: number;
  @Prop(Number) readonly year!: number;

  daysInMonth: number = new Date(
    this.year as number,
    this.month as number,
    0
  ).getDate();
}
</script>

<style lang="scss" scoped>
.days {
  transform: translateX(-20vmin);
  .day {
    position: absolute;
    width: 40vmin;
    text-align: right;
    font-size: calc(0.5rem + 0.5vmin);
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    transition: transform 0.5s ease, font-size 0.5s ease;
  }

  .active {
    font-size: calc(1rem + 0.5vmin);
  }
}
</style>
