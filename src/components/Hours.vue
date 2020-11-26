<template>
  <div class="hours">
    <p
      :class="{ active: n - 1 === hour }"
      class="hour date"
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
    width: 70vmin;
  }
}
</style>
