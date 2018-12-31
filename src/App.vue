<template>
  <svg width="350" height="150" viewBox="0 0 350 150">
    <Service x="50" y="15" width="50" height="30" label="Consolidator" />
    <Arrow x1="100" y1="30" x2="150" y2="30" />
    <Service x="150" y="15" width="50" height="30" label="Normality Generator" />
    <Service x="50" y="100" width="50" height="30" label="Recorder of Anomalies" />
    <Service x="150" y="100" width="50" height="30" label="Predictor" />
    <Service x="250" y="100" width="50" height="30" label="Alarm Generator" />
  </svg>
</template>

<script>
import Arrow from "./components/Arrow.vue";
import Service from "./components/Service.vue";

export default {
  name: "app",
  components: {
    Arrow,
    Service
  }
};
</script>

<style scoped>
svg {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  background-color: #fff8f0;
}
</style>
