<template>
  <div id="app">
    <QRCodeOption canvas="qrcode"/>
    <canvas id="qrcode" />
  </div>
</template>

<script>
import QRCodeOption from "./components/QRCodeOption.vue";

export default {
  name: "app",
  components: {
    QRCodeOption
  }
};
</script>

<style scoped>
</style>
