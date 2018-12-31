<template>
  <svg :x="x" :y="y" :width="width" :height="height" :viewBox="viewBox">
    <defs>
      <pattern id="pattern" width=".1" height="1">
        <animateTransform
          attributeName="patternTransform"
          type="translate"
          from="0"
          to="50"
          begin="2"
          dur="10s"
          repeatCount="indefinite"
          fill="freeze"
        ></animateTransform>
        <rect width="100%" height="100%" class="pattern-bg"></rect>
        <rect width="5%" :height="height" class="pattern-fg"></rect>
      </pattern>
    </defs>
    <rect
      :x="rectX"
      :y="rectY"
      :width="rectWidth"
      :height="rectHeight"
      :rx="rectRxy"
      :ry="rectRxy"
      :stroke-width="strokeWidth"
      fill="url(#pattern)"
      class="symbol"
    ></rect>
    <text
      x="50%"
      y="50%"
      text-anchor="middle"
      alignment-baseline="middle"
      v-html="multilineLabel"
      class="label"
    ></text>
  </svg>
</template>

<script>
export default {
  props: ["x", "y", "width", "height", "label"],
  data: () => ({}),
  computed: {
    viewBox() {
      return `0 0 ${this.width} ${this.height}`;
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
      return parseInt(this.height) - 2 * this.strokeWidth;
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
// @symbol-color: red;
@symbol-stroke-color: black;
@label-color: #2a0c4e;
@pattern-bg-color: #51355a;
@pattern-fg-color: #2a0c4e;

.symbol {
  // fill: @symbol-color;
  opacity: 0.7;
  stroke: @symbol-stroke-color;
  stroke-width: 1;
  stroke-opacity: 0.9;
}
.label {
  font-size: 0.4em;
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
