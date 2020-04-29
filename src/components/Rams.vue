<template>
  <div>
    <Listitem
      v-for="ram in ramsMapped"
      :key="getRamKey(ram)"
      :pcPartData="ram"
      :translations="ramLabels"
    ></Listitem>
  </div>
</template>
<script>
import Listitem from "./Listitem";
export default {
  name: "Rams",
  components: {
    Listitem
  },
  props: {
    ramList: Array,
    ramLabels: Array
  },
  data: function() {
    return { language: "ge" };
  },
  methods: {
    getRamKey: function(ram) {
      return ram.Brand + ram.Name + Math.floor(Math.random() * 1000);
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
