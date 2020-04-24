<template>
  <div class="hello">
    <Navbar></Navbar>
    <ul class="homelist">
      <li>პროცესორი (CPU) <button>ამოირჩიე</button></li>
      <li>ვიდეო ბარათი (GPU) <button>ამოირჩიე</button></li>
      <li>დედაბარათი (Motherboard) <button>ამოირჩიე</button></li>
      <li>მყარი დისკი (HDD) <button>ამოირჩიე</button></li>
      <li>ოპერატიული მეხსიერება (RAM) <button>ამოირჩიე</button></li>
    </ul>
  </div>
</template>

<script>
import Navbar from './Navbar';
export default {
  name: 'HelloWorld',
  props: {
    msg: String,
  },
  components: {
    Navbar,
  },
  data: function() {
    return {
      showCpus: false,
      showGpus: false,
      showMboard: false,
      showHdd: false,
      showRam: false,
    };
  },
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
  font-family: 'BPG Glaho WEB Caps', sans-serif;
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
</style>
