<template>
  <svg :x="x" :y="y" :width="boxWidth" :height="boxHeight" :viewBox="viewBox">
    <defs>
      <pattern id="pattern" width=".1" height="1">
        <animateTransform attributeName="patternTransform" attributeType="XML" type="rotate" from="45" to="360" begin="0" dur="60s" repeatCount="indefinite" />
        <rect width="100%" height="100%" fill="rgb(185, 235, 50)" />
        <rect width="5%" :height="boxHeight" fill="tomato" />
      </pattern>
    </defs>
    <rect :x="rectX" :y="rectY" :width="rectWidth" :height="rectHeight" :rx="rectRxy" :ry="rectRxy" :stroke-width="strokeWidth" fill="url(#pattern)" class="symbol" />
    <text x="50%" y="50%" text-anchor="middle" alignment-baseline="middle" v-html="multilineLabel" class="label" />
  </svg>
</template>

<script>
export default {
  props: ["x", "y", "width", "label"],
  data: () => ({
    boxWidth: 50
  }),
  computed: {
    viewBox() {
      return `0 0 ${this.boxWidth} ${this.boxHeight}`;
    },
    boxHeight() {
      return this.boxWidth / 2;
    },
    rectRxy() {
      return this.boxWidth / 2;
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
    fontSize() {
      return this.boxWidth * 0.11;
    },
    strokeWidth() {
      return this.boxWidth * 0.005;
    },
    multilineLabel() {
      let words = this.label.split(/\s+/);
      let dy = (0.5 - (words.length - 1) * 1.0) / 2;
      // debugger
      return words
        .map(
          (word, index) =>
            `<tspan x="50%" dy="${index == 0 ? dy : 1.0}em">${word}</tspan>`
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
.symbol {
  /* fill: url(#Pattern); */
  opacity: 0.7;
  stroke: black;
  stroke-opacity: 0.9;
}
.label {
  font-size: 0.3em;
  font-weight: bold;
  opacity: 0.9;
}
/* #Pattern {
  transform: rotate(45deg);
} */
/* #Pattern > rect {
  fill: rgb(185, 235, 50);
} */
</style>
