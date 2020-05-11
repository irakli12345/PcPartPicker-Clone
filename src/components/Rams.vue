<template>
  <div>
    <Filterlist
      :suppliedList="ramList"
      :orderOfFilter="orderOfFilter"
      :filterTranslations="filterTranslations"
      @filter="handleFilter"
    ></Filterlist>
    <Listitem
      v-for="ram in ramsMapped"
      :key="getRamKey(ram)"
      :pcPartData="ram"
      :translations="ramLabels"
      @selected="handleSelected(ram[0])"
      :selectedItem="selectedRam"
    ></Listitem>
  </div>
</template>
<script>
import Listitem from "./Listitem";
import Filterlist from "./Filterlist";
export default {
  name: "Rams",
  components: {
    Listitem,
    Filterlist
  },
  props: {
    ramList: Array,
    ramLabels: Array,
    selectedRam: String,
    filterTranslations: Object
  },
  data: function() {
    return {
      language: "ge",
      orderOfFilter: ["Brand", "Name", "Speed", "capacityInGbs", "price"]
    };
  },
  methods: {
    getRamKey: function(ram) {
      return ram.Brand + ram.Name + Math.floor(Math.random() * 1000);
    },
    handleSelected: function(ramName) {
      this.$emit("selected", ramName);
    },
    handleFilter: function(object) {
      console.log(object);
    }
  },
  computed: {
    ramsMapped: function() {
      let arr = [];
      let innerArr = [];
      for (let i = 0; i < this.ramList.length; i++) {
        innerArr.push(this.ramList[i].Brand + " " + this.ramList[i].Name);
        innerArr.push(this.ramList[i].Speed);
        innerArr.push(this.ramList[i].capacityInGbs + "GB");
        innerArr.push(this.ramList[i].capacityOfEach + "GB");
        innerArr.push(this.ramList[i].price + "₾");
        arr.push(innerArr);
        innerArr = [];
      }

      return arr;
    }
  }
};
</script>
<style></style>
