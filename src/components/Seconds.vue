<template>
  <div class="seconds">
    <p
      :class="{ active: n - 1 === second }"
      class="second"
      :style="{
        transform: 'rotate(' + ((second - n + 1) * 360) / 60 + 'deg)'
      }"
      v-for="n in 60"
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
  @Prop(Number) readonly second!: number;
}
</script>

<style lang="scss" scoped>
.seconds {
  transform: translateX(-45vmin);
  .second {
    position: absolute;
    width: 90vmin;
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
