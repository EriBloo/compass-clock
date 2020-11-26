<template>
  <div class="days">
    <p
      :class="{ active: n === day }"
      class="day date"
      :style="{
        transform: 'rotate(' + (day - n) * (360 / daysInMonth) + 'deg)'
      }"
      v-for="n in daysInMonth"
      :key="n"
    >
      {{ n }}
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Day extends Vue {
  @Prop(Number) readonly day!: number;
  @Prop(Number) readonly month!: number;
  @Prop(Number) readonly year!: number;

  daysInMonth: number = new Date(this.year, this.month, 0).getDate() - 1;
}
</script>

<style lang="scss" scoped>
.days {
  transform: translateX(-20vmin);
  .day {
    width: 40vmin;
  }
}
</style>
