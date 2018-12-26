<template>
  <svg :x="x" :y="y" :width="width" :height="height">
    <rect :width="width" :height="height" :fill="fill" rx="10" ry="10" />
    <text x="50%" y="50%" class="text" text-anchor="middle" alignment-baseline="middle" v-html="multilineLabel"></text>
  </svg>
</template>

<script>
export default {
  props: ["x", "y", "width", "height", "fill", "label"],
  data: () => ({}),
  computed: {
    multilineLabel() {
      let words = this.label.split(/\s+/);
      let dy = (0.5 /*horizontal center*/ - (words.length - 1) * 1.2) / 2;
      return words
        .map((word, index) => `<tspan x="50%" dy="${index == 0 ? dy : 1.2}em">${word}</tspan>`)
        .join("");
    },
    translate() {
      return `translate(${this.x} ${this.y})`; // back ticks = string template
    }
  }
};
</script>

<style scoped>
.text {
  font-size: 3px;
}
</style>
