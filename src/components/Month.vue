<template>
  <div class="months">
    <p
      :class="{ active: n - 1 === month }"
      class="month date"
      :style="{
        transform: 'rotate(' + (month - n + 1) * (360 / 12) + 'deg)'
      }"
      v-for="n in 12"
      :key="n"
    >
      {{ months[n - 1] }}
    </p>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Month extends Vue {
  @Prop(Number) readonly month!: number;

  months: { [month: number]: string } = {
    0: "Jan",
    1: "Feb",
    2: "Mar",
    3: "Apr",
    4: "May",
    5: "Jun",
    6: "Jul",
    7: "Aug",
    8: "Sep",
    9: "Oct",
    10: "Nov",
    11: "Dec"
  };
}
</script>

<style lang="scss" scoped>
.months {
  transform: translateX(-25vmin);
  .month {
    width: 50vmin;
  }
}
</style>
