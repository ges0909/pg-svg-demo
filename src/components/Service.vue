<template>
  <g :transform="translate">
    <rect :width="width" :height="height" :fill="fill" rx="10" ry="10" />
    <!-- <g transform="translate(50% 50%)"> -->
    <text class="text" text-anchor="middle">{{ label }}</text>
    <!-- </g> -->
  </g>
</template>

<script>
export default {
  props: ["x", "y", "width", "height", "fill", "label"],
  computed: {
    translate() {
      return `translate(${this.x} ${this.y})`;
    }
  }
};
</script>

<style scoped>
.text {
  font-size: 3px;
}
</style>