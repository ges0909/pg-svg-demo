<template>
  <div id="app">
    <svg
      viewBox="0 0 100 100"
      preserveAspectRatio="none"
    >
      <rect
        x="0"
        y="0"
        width="100%"
        height="100%"
        fill="grey"
      />
    </svg>
  </div>
</template>

<script>
export default {
  name: "app"
};
</script>

<style>
svg {
  position: fixed;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
}
</style>
