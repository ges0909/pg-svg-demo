<template>
  <svg viewBox="0 0 100 100"> <!-- preserveAspectRatio="align" -->
    <Service x="10" y="10" label="Consolidator" />
    <Service x="10" y="50" label="Normality Generator" />
    <Service x="30" y="30" label="Recorder of Anomalies" />
    <Service x="50" y="10" label="Predictor" />
    <Service x="50" y="50" label="Alarm Generator" />
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
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}
</style>
