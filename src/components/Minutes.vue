<template>
  <div class="minutes">
    <p
      :class="{ active: n - 1 === minute }"
      class="minute"
      :style="{
        transform: 'rotate(' + (minute - n + 1) * (360 / 60) + 'deg)'
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
export default class Minutes extends Vue {
  @Prop(Number) readonly minute!: number;
}
</script>

<style lang="scss" scoped>
.minutes {
  transform: translateX(-40vmin);
  .minute {
    position: absolute;
    width: 80vmin;
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
