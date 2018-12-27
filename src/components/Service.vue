<template>
  <svg :x="x" :y="y" :width="boxWidth" :height="boxHeight" :viewBox="viewBox">
    <rect :x="rectX" :y="rectY" :width="rectWidth" :height="rectHeight" :rx="rectRxy" :ry="rectRxy" :stroke-width="strokeWidth" vector-effect="non-scaling-stroke" />
    <text x="50%" y="50%" text-anchor="middle" alignment-baseline="middle" v-html="multilineLabel" />
  </svg>
</template>

<script>
export default {
  props: ["x", "y", "label"],
  data: () => ({
    boxWidth: 30,
    boxHeight: 20,
    rectRxy: 15,
    strokeWidth: 1
  }),
  computed: {
    viewBox() {
      return `0 0 ${this.boxWidth} ${this.boxHeight}`;
    },
    rectX() {
      return this.strokeWidth;
    },
    rectY() {
      return this.strokeWidth;
    },
    rectWidth() {
      return parseInt(this.boxWidth) - 2 * this.strokeWidth;
    },
    rectHeight() {
      return parseInt(this.boxHeight) - 2 * this.strokeWidth;
    },
    multilineLabel() {
      let words = this.label.split(/\s+/);
      let dy = (0.5 - (words.length - 1) * 1.2) / 2;
      // debugger
      return words
        .map(
          (word, index) =>
            `<tspan x="50%" dy="${index == 0 ? dy : 1.2}em">${word}</tspan>`
        )
        .join("");
    },
    translate() {
      return `translate(${this.x} ${this.y})`;
    }
  }
};
</script>

<style scoped>
rect {
  fill: tomato;
  opacity: 0.7;
  stroke: black;
  stroke-opacity: 0.9;
}
text {
  font-size: 3px;
  font-weight: bolder;
}
</style>
