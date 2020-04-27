<template>
  <div>
    <Listitem v-for="ram in ramList" :key="getRamKey(ram)" :ram="ram"></Listitem>
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
  }
};
</script>
<style></style>
