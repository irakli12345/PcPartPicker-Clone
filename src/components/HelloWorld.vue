<template>
  <div class="hello">
    <Navbar></Navbar>
    <ul class="homelist" v-if="pcParts">
      <li>
        პროცესორი (CPU)
        <button @click="cpuchecked = !cpuchecked">ამოირჩიე</button>
        <b>{{ addedPcParts.cpu }}</b>
        <button
          v-show="addedPcParts.cpu"
          @click="addedPcParts.cpu = ''"
          class="discardButton"
        >გაუქმება</button>
      </li>
      <div v-if="cpuchecked">
        <Cpus
          :cpuList="pcParts.cpus"
          :cpuLabels="translations.listItem.cpu"
          @selected="handleCpuAddedToCart"
          :selectedCpu="addedPcParts.cpu"
          :filterTranslations="translations.filterLabels.cpu"
        ></Cpus>
      </div>
      <li>
        ვიდეო ბარათი (GPU)
        <button @click="gpuchecked = !gpuchecked">ამოირჩიე</button>
        <b>{{ addedPcParts.gpu }}</b>
        <button
          v-show="addedPcParts.gpu"
          @click="addedPcParts.gpu = ''"
          class="discardButton"
        >გაუქმება</button>
      </li>
      <div v-if="gpuchecked">
        <Gpus
          :gpuList="pcParts.gpus"
          :gpuLabels="translations.listItem.gpu"
          @selected="handleGpuAddedToCart"
          :selectedGpu="addedPcParts.gpu"
          :filterTranslations="translations.filterLabels.gpu"
        ></Gpus>
      </div>
      <li>
        დედაბარათი (Motherboard)
        <button @click="mboardschecked = !mboardschecked">ამოირჩიე</button>
        <b>{{ addedPcParts.mboard }}</b>
        <button
          v-show="addedPcParts.mboard"
          @click="addedPcParts.mboard = ''"
          class="discardButton"
        >გაუქმება</button>
      </li>
      <div v-if="mboardschecked">
        <Mboards
          :mboardList="pcParts.mboards"
          :mboardLabels="translations.listItem.mboard"
          @selected="handleMboardSelected"
          :selectedMboard="addedPcParts.mboard"
          :filterTranslations="translations.filterLabels.mboard"
        ></Mboards>
      </div>
      <li>
        მყარი დისკი (HDD)
        <button @click="hddchecked = !hddchecked">ამოირჩიე</button>
        <b>{{ addedPcParts.hdd }}</b>
        <button
          v-show="addedPcParts.hdd"
          @click="addedPcParts.hdd = ''"
          class="discardButton"
        >გაუქმება</button>
      </li>
      <div v-if="hddchecked">
        <Hdds
          :hddList="pcParts.hdds"
          :hddLabels="translations.listItem.hdd"
          @selected="handleHddSelected"
          :selectedHdd="addedPcParts.hdd"
          :filterTranslations="translations.filterLabels.hdd"
        ></Hdds>
      </div>
      <li>
        ოპერატიული მეხსიერება (RAM)
        <button @click="ramchecked = !ramchecked">ამოირჩიე</button>
        <b>{{ addedPcParts.ram }}</b>
        <button
          v-show="addedPcParts.ram"
          @click="addedPcParts.ram = ''"
          class="discardButton"
        >გაუქმება</button>
      </li>
      <div v-if="ramchecked">
        <Rams
          :ramList="pcParts.rams"
          :ramLabels="translations.listItem.ram"
          @selected="handleRamSelected"
          :selectedRam="addedPcParts.ram"
          :filterTranslations="translations.filterLabels.ram"
        ></Rams>
      </div>
    </ul>
  </div>
</template>

<script>
import Navbar from "./Navbar";
import Hdds from "./Hdds";
import Gpus from "./Gpus";
import Cpus from "./Cpus";
import Mboards from "./Mboards";
import Rams from "./Rams";
export default {
  name: "HelloWorld",
  props: {
    msg: String
  },
  components: {
    Navbar,
    Hdds,
    Gpus,
    Cpus,
    Mboards,
    Rams
  },
  data: function() {
    return {
      cpuchecked: false,
      gpuchecked: false,
      mboardschecked: false,
      hddchecked: false,
      ramchecked: false,
      pcParts: null,
      translations: null,
      addedPcParts: { cpu: "", gpu: "", ram: "", hdd: "", mboard: "" }
    };
  },
  mounted: function() {
    fetch("http://localhost:3000/pcparts")
      .then(res => res.json())
      .then(json => (this.pcParts = json[0]));
    fetch("http://localhost:3000/translations")
      .then(res => res.json())
      .then(json => (this.translations = json));
  },
  methods: {
    handleCpuAddedToCart: function(cpuName) {
      if (this.addedPcParts.cpu) {
        this.addedPcParts.cpu = null;
      } else {
        this.addedPcParts.cpu = cpuName;
      }
    },
    handleGpuAddedToCart: function(gpuName) {
      if (this.addedPcParts.gpu) {
        this.addedPcParts.gpu = null;
      } else {
        this.addedPcParts.gpu = gpuName;
      }
    },
    handleMboardSelected: function(mboardName) {
      if (this.addedPcParts.mboard) {
        this.addedPcParts.mboard = null;
      } else {
        this.addedPcParts.mboard = mboardName;
      }
    },
    handleHddSelected: function(hddName) {
      if (this.addedPcParts.hdd) {
        this.addedPcParts.hdd = null;
      } else {
        this.addedPcParts.hdd = hddName;
      }
    },
    handleRamSelected: function(ramName) {
      if (this.addedPcParts.ram) {
        this.addedPcParts.ram = null;
      } else {
        this.addedPcParts.ram = ramName;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
:root {
  --primary: rgb(252, 81, 48);
  --primaryh: rgb(255, 108, 96);
  --secondary: rgb(67, 188, 205);
  --secondaryh: rgb(156, 234, 239);
  --tertiary: rgb(134, 222, 183);
}
* {
  font-family: "BPG Glaho WEB Caps", sans-serif;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
.homelist li {
  background-color: white;
  padding: 1rem;
  border-bottom: 2px solid lightgrey;
  width: 50%;
  margin: auto;
  margin-top: 1rem;
}
.homelist li button {
  padding: 0.5rem 1rem;
  box-shadow: none;
  border: none;
  background-color: var(--tertiary);
  border-radius: 1rem;
}
a {
  color: #42b983;
}
.discardButton {
  background-color: rgb(255, 108, 96) !important;
}
</style>
