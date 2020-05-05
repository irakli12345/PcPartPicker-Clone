<template>
  <div>
    <Listitem
      v-for="hdd in hddsMapped"
      :key="getHddKey(hdd)"
      :translations="hddLabels"
      :pcPartData="hdd"
      @selected="handleSelected(hdd[0])"
      :selectedItem="selectedHdd"
    ></Listitem>
  </div>
</template>
<script>
import Listitem from "./Listitem";
export default {
  name: "Hdds",
  components: {
    Listitem
  },
  props: {
    hddList: Array,
    hddLabels: Array,
    selectedHdd: String
  },
  data: function() {
    return {};
  },
  methods: {
    getHddKey: function(hdd) {
      return hdd.brand + hdd.name + Math.floor(Math.random() * 1000);
    },
    handleSelected: function(hddName) {
      this.$emit("selected", hddName);
    }
  },
  computed: {
    hddsMapped: function() {
      let arr = [];
      let innerArr = [];
      let capacityValue = null;
      for (let i = 0; i < this.hddList.length; i++) {
        innerArr.push(this.hddList[i].brand + " " + this.hddList[i].name);
        capacityValue = (capacity =>
          capacity >= 1024 ? capacity / 1024 + "TB" : capacity + "GB")(
          this.hddList[i].capacityInGbs
        );
        innerArr.push(capacityValue);
        innerArr.push(this.hddList[i].RPM || this.hddList[i].type);
        arr.push(innerArr);
        innerArr = [];
      }

      return arr;
    }
  }
};
</script>
<style></style>
