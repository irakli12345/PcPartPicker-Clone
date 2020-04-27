<template>
  <div>
    <h3 v-for="hdd in hddList" :key="getHddKey(hdd)">{{ hdd.brand + ' ' + hdd.name }}</h3>
  </div>
</template>
<script>
export default {
  name: "Hdds",
  props: {
    hddList: Array,
    hddLabels: Array
  },
  data: function() {
    return {};
  },
  methods: {
    getHddKey: function(hdd) {
      return hdd.brand + hdd.name + Math.floor(Math.random() * 1000);
    }
  }
};
</script>
<style></style>
