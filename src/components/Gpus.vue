<template>
  <div>
    <h1>Here go the Gpus</h1>
    <h3 v-for="gpu in gpuList" :key="getGpuKey(gpu)">{{ gpu.brand + ' ' + gpu.name }}</h3>
  </div>
</template>
<script>
export default {
  name: "Gpus",
  data: function() {
    return {};
  },
  props: {
    gpuList: Array,
    gpuLabels: Array
  },
  methods: {
    getGpuKey(gpu) {
      return gpu.brand + gpu.name + Math.floor(Math.random() * 1000);
    }
  }
};
</script>
<style></style>
