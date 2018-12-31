<template>
  <svg :x="x1" :y="y1" :width="width" :height="height" :viewBox="viewBox">
    <polygon :points="points" class="symbol" />
  </svg>
</template>

<script>
export default {
  props: ["x1", "y1", "x2", "y2"],
  data: () => ({
    arrowWidth: 15
  }),
  computed: {
    width() {
      return `${this.x2 - this.x1}`;
    },
    height() {
      return `${this.y2 - this.y1 + this.arrowWidth}`;
    },
    viewBox() {
      return `${this.x1} ${this.y1 - this.height / 2} ${this.width} ${
        this.height
      }`;
    },
    points() {
      return `${this.X0} ${this.X1} ${this.X2} ${this.X3} ${this.X4} ${this.X5} ${this.X6} ${this.X7}`;
    },
    X0() {
      return `${this.x1},${this.y1}`;
    },
    X1() {
      return `${this.x1},${this.y1 - this.arrowWidth / 4}`;
    },
    X2() {
      return `${this.x2 - this.arrowWidth / 4},${this.y1 - this.arrowWidth / 4}`;
    },
    X3() {
      return `${this.x2 - this.arrowWidth / 4},${this.y2 - this.arrowWidth / 2}`;
    },
    X4() {
      return `${this.x2},${this.y2}`;
    },
    X5() {
      return `${this.x2 - this.arrowWidth / 4},${Number(this.y2) + this.arrowWidth / 2}`;
    },
    X6() {
      return `${this.x2 - this.arrowWidth / 4},${Number(this.y2) + this.arrowWidth / 4}`;
    },
    X7() {
      return `${this.x1},${Number(this.y1) + this.arrowWidth / 4}`;
    }
  }
};
</script>

<style lang="less" scoped>
@symbol-color: grey;
@symbol-stroke-color: black;

.symbol {
  fill: @symbol-color;
  opacity: 0.7;
  stroke: @symbol-stroke-color;
  stroke-width: 1;
  stroke-opacity: 0.9;
}
</style>