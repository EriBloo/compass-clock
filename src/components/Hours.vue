<template>
  <div class="hours">
    <p
      :class="{ active: n - 1 === hour }"
      class="hour"
      :style="{
        transform: 'rotate(' + (hour - n + 1) * (360 / 24) + 'deg)'
      }"
      v-for="n in 24"
      :key="n"
    >
      {{ n - 1 }}
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Hours extends Vue {
  @Prop(Number) readonly hour!: number;
}
</script>

<style lang="scss" scoped>
.hours {
  transform: translateX(-35vmin);
  .hour {
    position: absolute;
    width: 70vmin;
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
