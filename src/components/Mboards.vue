<template>
  <div>
    <Listitem
      v-for="mboard in mboardsMapped"
      :key="generateMboardKey(mboard[0])"
      :translations="mboardLabels"
      :pcPartData="mboard"
      @selected="displaySelected(mboard[0])"
      :selectedItem="selectedMboard"
    ></Listitem>
  </div>
</template>
<script>
import Listitem from "./Listitem";
export default {
  name: "Mboards",
  components: {
    Listitem
  },
  props: {
    mboardList: Array,
    mboardLabels: Array,
    selectedMboard: String
  },
  data: function() {
    return {};
  },
  methods: {
    generateMboardKey: function(mboardName) {
      return mboardName + Math.floor(Math.random() * 1000);
    },
    displaySelected: function(mboardName) {
      this.$emit("selected", mboardName);
    }
  },
  computed: {
    mboardsMapped: function() {
      let arr = [];
      let innerArr = [];
      for (let i = 0; i < this.mboardList.length; i++) {
        innerArr.push(this.mboardList[i].brand + this.mboardList[i].name);
        innerArr.push(this.mboardList[i].maxRam + "GB");
        innerArr.push(this.mboardList[i].ramSlots);
        innerArr.push(this.mboardList[i].socket);
        innerArr.push(this.mboardList[i].price + "₾");
        arr.push(innerArr);
        innerArr = [];
      }

      return arr;
    }
  }
};
</script>
<style></style>
