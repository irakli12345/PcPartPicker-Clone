<template>
  <div>
    <Filterlist
      :suppliedList="hddList"
      :orderOfFilter="orderOfFilter"
      :filterTranslations="filterTranslations"
      @filter="handleFilter"
    ></Filterlist>
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
import Filterlist from "./Filterlist";
export default {
  name: "Hdds",
  components: {
    Listitem,
    Filterlist
  },
  props: {
    hddList: Array,
    hddLabels: Array,
    selectedHdd: String,
    filterTranslations: Object
  },
  data: function() {
    return {
      orderOfFilter: ["brand", "capacityInGbs", "name", "type"]
    };
  },
  methods: {
    getHddKey: function(hdd) {
      return hdd.brand + hdd.name + Math.floor(Math.random() * 1000);
    },
    handleSelected: function(hddName) {
      this.$emit("selected", hddName);
    },
    handleFilter: function(object) {
      console.log(object);
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
