<template>
  <svg viewBox="0 0 350 150"> <!-- preserveAspectRatio="align" -->
    <Service x="50" y="15" width="50" label="Consolidator" />
    <Service x="150" y="15" width="50" label="Normality Generator" />
    <Service x="50" y="100" width="50" label="Recorder of Anomalies" />
    <Service x="150" y="100" width="50" label="Predictor" />
    <Service x="250" y="100" width="50" label="Alarm Generator" />
  </svg>
</template>

<script>
import Service from "./components/Service.vue";

export default {
  name: "app",
  components: {
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
  background-color: gray
}
</style>
