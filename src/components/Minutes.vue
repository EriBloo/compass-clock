<template>
  <div class="minutes">
    <p
      :class="{ active: n - 1 === minute }"
      class="minute date"
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
    width: 80vmin;
  }
}
</style>
