<template>
  <div>
    <Listitem
      v-for="cpu in cpusMapped"
      :pcPartData="cpu"
      :key="getCpuKey(cpu)"
      :translations="cpuLabels"
    ></Listitem>
  </div>
</template>
<script>
import Listitem from "./Listitem";
export default {
  name: "Cpus",
  props: {
    cpuList: Array,
    cpuLabels: Array
  },
  components: {
    Listitem
  },
  data: function() {
    return {};
  },
  methods: {
    getCpuKey: function(cpu) {
      return cpu.brand + " " + Math.floor(Math.random() * 1000);
    }
  },
  computed: {
    cpusMapped: function() {
      let arr = [];
      let innerArr = [];
      for (let i = 0; i < this.cpuList.length; i++) {
        innerArr.push(this.cpuList[i].brand + this.cpuList[i].series);
        innerArr.push(this.cpuList[i]["core count"]);
        innerArr.push(this.cpuList[i]["integrated-graphics"]);
        innerArr.push(this.cpuList[i].socket);
        innerArr.push(this.cpuList[i].price + "₾");
        arr.push(innerArr);
        innerArr = [];
      }

      return arr;
    }
  }
};
</script>
<style></style>
