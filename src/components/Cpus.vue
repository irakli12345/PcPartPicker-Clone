<template>
  <div>
    <Filterlist
      :suppliedList="cpuList"
      :orderOfFilter="orderOfFilter"
      :filterTranslations="filterTranslations"
      @filter="handleFilter"
    ></Filterlist>
    <Listitem
      v-for="cpu in cpusMapped"
      :pcPartData="cpu"
      :key="getCpuKey(cpu)"
      :translations="cpuLabels"
      @selected="displaySelected(cpu[0])"
      :selectedItem="selectedCpu"
    ></Listitem>
  </div>
</template>
<script>
import Filterlist from "./Filterlist";
import Listitem from "./Listitem";
export default {
  name: "Cpus",
  props: {
    cpuList: Array,
    cpuLabels: Array,
    selectedCpu: String,
    filterTranslations: Object
  },
  components: {
    Listitem,
    Filterlist
  },
  data: function() {
    return {
      orderOfFilter: [
        "brand",
        "series",
        "integrated-graphics",
        "socket",
        "price"
      ],
      filteredCpuList: []
    };
  },
  methods: {
    getCpuKey: function(cpu) {
      return cpu.brand + " " + Math.floor(Math.random() * 1000);
    },
    displaySelected: function(cpuName) {
      this.$emit("selected", cpuName);
    },
    handleFilter: function(object) {
      console.log(object);
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
