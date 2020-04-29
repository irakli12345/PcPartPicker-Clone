<template>
  <div>
    <Listitem
      v-for="gpu in gpusMapped"
      :key="getGpuKey(gpu)"
      :translations="gpuLabels"
      :pcPartData="gpu"
    >{{ gpu.brand + ' ' + gpu.name }}</Listitem>
  </div>
</template>
<script>
import Listitem from "./Listitem";
export default {
  name: "Gpus",
  data: function() {
    return {};
  },
  components: {
    Listitem
  },
  props: {
    gpuList: Array,
    gpuLabels: Array
  },
  methods: {
    getGpuKey(gpu) {
      return gpu.brand + gpu.name + Math.floor(Math.random() * 1000);
    }
  },
  computed: {
    gpusMapped: function() {
      let arr = [];
      let innerArr = [];
      for (let i = 0; i < this.gpuList.length; i++) {
        innerArr.push(this.gpuList[i].brand + this.gpuList[i].chipset);
        innerArr.push(this.gpuList[i].memoryInGbs + "GB");
        innerArr.push(this.gpuList[i].price + "₾");
        arr.push(innerArr);
        innerArr = [];
      }

      return arr;
    }
  }
};
</script>
<style></style>
