<template>
  <svg viewBox="0 0 100 100" preserveAspectRatio="none">
    <Service x="10" y="10" width="20" height="15" fill="grey" label="Consolidator" />
    <Service x="10" y="50" width="20" height="15" fill="red" label="Normality Generator" />
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
