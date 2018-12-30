<template>
  <svg :x="x" :y="y" :width="width" :height="boxHeight" :viewBox="viewBox">
    <defs>
      <pattern id="pattern" width=".1" height="1">
        <animateTransform attributeName="patternTransform" type="translate" from="0" to="50" begin="2" dur="10s" repeatCount="indefinite" fill="freeze" />
        <rect width="100%" height="100%" class="pattern-bg" />
        <rect width="5%" :height="boxHeight" class="pattern-fg" />
      </pattern>
    </defs>
    <rect :x="rectX" :y="rectY" :width="rectWidth" :height="rectHeight" :rx="rectRxy" :ry="rectRxy" :stroke-width="strokeWidth" fill="url(#pattern)" class="symbol" />
    <text x="50%" y="50%" text-anchor="middle" alignment-baseline="middle" v-html="multilineLabel" class="label" />
  </svg>
</template>

<script>
export default {
  props: ["x", "y", "width", "label"],
  data: () => ({}),
  computed: {
    viewBox() {
      return `0 0 ${this.width} ${this.boxHeight}`;
    },
    boxHeight() {
      return this.width / 2;
    },
    rectRxy() {
      return this.width / 2;
    },
    rectX() {
      return this.strokeWidth;
    },
    rectY() {
      return this.strokeWidth;
    },
    rectWidth() {
      return parseInt(this.width) - 2 * this.strokeWidth;
    },
    rectHeight() {
      return parseInt(this.boxHeight) - 2 * this.strokeWidth;
    },
    fontSize() {
      return this.width * 0.11;
    },
    strokeWidth() {
      return this.width * 0.005;
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
    }
    /*
    translate() {
      return `translate(${this.x} ${this.y})`;
    }
    */
  }
};
</script>

<style lang="less" scoped>
@symbol-stroke-color: black;
@label-color: #2a0c4e;
@pattern-bg-color: #51355a;
@pattern-fg-color: #2a0c4e;

.symbol {
  opacity: 0.7;
  stroke: @symbol-stroke-color;
  stroke-opacity: 0.9;
}
.label {
  font-size: 0.3em;
  fill: @label-color;
  font-weight: bold;
  opacity: 0.9;
}
.pattern-bg {
  fill: @pattern-bg-color;
}
.pattern-fg {
  fill: @pattern-fg-color;
}
</style>
