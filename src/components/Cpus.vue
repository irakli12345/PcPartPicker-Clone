<template>
  <div>
    <h3 v-for="cpu in cpuList" :key="getCpuKey(cpu)">
      {{ cpu.brand + cpu.series }} // Cores : {{ cpu['core count'] }} //
      Integrated Graphics :
      <span
        v-if="cpu['integrated-graphics']"
      >
        {{
        cpu['integrated-graphics']
        }}
      </span>
      <span v-else>None</span>
    </h3>
  </div>
</template>
<script>
export default {
  name: "Cpus",
  props: {
    cpuList: Array,
    cpuLabels: Array
  },
  data: function() {
    return {};
  },
  methods: {
    getCpuKey: function(cpu) {
      return cpu.brand + " " + Math.floor(Math.random() * 1000);
    }
  }
};
</script>
<style></style>
