<template>
  <div class="nav">
    <div class="logo">
      <a href="/">
        <i class="fas fa-home"></i>
      </a>
    </div>
    <ul class="menu">
      <a href="/build-a-pc">
        <li>კომპიუტერის აწყობა</li>
      </a>
      <a href="/ready-builds">
        <li>აწყობილი სისტემები</li>
      </a>
      <a href="/faq">
        <li>ხშირად დასმ. კითხვები</li>
      </a>
      <a href="contact-us">
        <li>კონტაქტი</li>
      </a>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Navbar",
  data: function() {
    return {};
  }
};
</script>
<style>
:root {
  --primary: rgb(252, 81, 48);
  --primaryh: rgb(255, 108, 96);
  --secondary: rgb(67, 188, 205);
  --secondaryh: rgb(156, 234, 239);
  --tertiary: rgb(134, 222, 183);
}
.menu {
  display: flex;
  justify-content: space-around;
  flex-grow: 3;
  margin: 0;
  padding: 0;
}
.nav {
  display: flex;
  justify-content: space-around;
  background-color: var(--primary);
  padding: 1rem;
}
.logo {
  flex-basis: 20%;
  width: auto;
}
.logo a {
  color: white;
}
.menu li {
  list-style: none;
  color: white;
  padding: 0.5rem 1rem;
  border-radius: 1rem;
}
.menu li:hover {
  background-color: var(--primaryh);
}
a {
  text-decoration: none;
}
</style>
