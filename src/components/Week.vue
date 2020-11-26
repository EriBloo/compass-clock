<template>
  <div class="weeks">
    <p
      :class="{ active: n - 1 === week }"
      class="week date"
      :style="{
        transform: 'rotate(' + (week - n + 1) * (360 / 7) + 'deg)'
      }"
      v-for="n in 7"
      :key="n"
    >
      {{ weeks[n - 1] }}
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Week extends Vue {
  @Prop(Number) readonly week!: number;

  weeks: { [week: number]: string } = {
    0: "Sun",
    1: "Mon",
    2: "Tue",
    3: "Wed",
    4: "Thu",
    5: "Fri",
    6: "Sat"
  };
}
</script>

<style lang="scss" scoped>
.weeks {
  transform: translateX(-15vmin);
  .week {
    width: 30vmin;
  }
}
</style>
