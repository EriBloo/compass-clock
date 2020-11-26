<template>
  <div class="seconds">
    <p
      :class="{ active: n - 1 === second }"
      class="second date"
      :style="{
        transform: 'rotate(' + (second - n + 1) * (360 / 60) + 'deg)'
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
    width: 90vmin;
  }
}
</style>
