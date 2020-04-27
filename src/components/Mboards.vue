<template>
  <div>
    <h3
      v-for="mboard in mboardList"
      :key="generateMboardKey(mboard)"
    >{{ mboard.brand + mboard.name }}</h3>
  </div>
</template
>
<script>
export default {
  name: "Mboards",
  props: {
    mboardList: Array,
    mboardLabels: Array
  },
  data: function() {
    return {};
  },
  methods: {
    generateMboardKey: function(mboard) {
      return mboard.brand + mboard.name + Math.floor(Math.random() * 1000);
    }
  }
};
</script>
<style></style>
