<template>
  <div>
    <form>
      <div v-for="filterLabel in orderOfFilter" :key="generateKey(filterLabel)">
        <label>{{filterTranslations[filterLabel][language]}}</label>
        <select v-model="selected[filterLabel]">
          <option
            v-for="thing in removeDuplicates(suppliedList, orderOfFilter)[filterLabel]"
            :key="generateKey(thing)"
          >{{thing}}</option>
        </select>
      </div>
    </form>
    <div>
      <button @click="$emit('filter', selected)">გაფილტვრა</button>
      <button v-if="Object.keys(selected).length" @click="selected = {}">გაუქმება</button>
    </div>
  </div>
</template>
<script>
export default {
  data: function() {
    return {
      language: "en",
      selected: {}
    };
  },
  props: {
    suppliedList: Array,
    orderOfFilter: Array,
    filterTranslations: Object
  },
  methods: {
    generateKey: function(string) {
      return string + Math.random() * 100000;
    },
    removeDuplicates(objectList, filterLabelsList) {
      let obj = {};
      for (const label of filterLabelsList) {
        obj[label] = [];
        for (const object of objectList) {
          if (obj[label].indexOf(object[label]) == -1) {
            obj[label].push(object[label]);
          }
        }
      }
      return obj;
    }
  },
  mounted: function() {}
};
</script>
<style scoped>
form {
  margin: auto;
  padding: 3px;
  width: 70%;
  display: flex;
  justify-content: space-around;
}
label {
  margin-right: 1rem;
}
select {
}
button {
  margin-left: 1rem;
  color: black;
  padding: 0.5rem 1rem;
  box-shadow: none;
  border: none;
  background-color: var(--tertiary);
  border-radius: 1rem;
}
* {
  font-family: "BPG Glaho WEB Caps", sans-serif;
}
</style>
