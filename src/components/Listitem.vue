<template>
  <div class="main">
    <div>
      <b>ბრენდი და ჩიპსეტი:</b> Gigabyte GeForce RTX 2070 SUPER
    </div>
    <div>
      <b>მახსოვრობა:</b> 8GB
    </div>
    <div>
      <b>ფასი:</b> 1200₾
    </div>
    <div class="cartButton">
      <span
        :class="[addedToCart ? 'aroundCartAfterClick' : 'aroundCart']"
        @click="addedToCart = !addedToCart"
      >
        <div :class="[addedToCart ? 'fa-shopping-cart-color' : '', 'wrapperDiv']">
          <i :class="[ 'fas', 'fa-shopping-cart']"></i>
        </div>
      </span>
      <p v-if="addedToCart" style="margin-left: 3px">
        <b>Selected</b>
      </p>
    </div>
  </div>
</template>
<script>
export default {
  name: "Listitem",
  data: function() {
    return { addedToCart: false };
  },
  props: {}
};
</script>
<style>
.main {
  height: 2rem;
  width: 50%;
  border: 2px solid yellow;
  margin: auto;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem;
  align-items: center;
}
.wrapperDiv {
  display: inline-block;
}
.cartButton {
  width: 15%;
  display: flex;
}
.aroundCart {
  background-color: #cbe896;
  padding: 1rem;
  border-radius: 50%;
}
.aroundCartAfterClick {
  background-color: #92c57a;
  padding: 1rem;
  border-radius: 50%;
}

.fa-shopping-cart-color {
  color: white !important;
}
@media screen and (min-width: 720px) {
  .main {
    padding: 0.5rem 5rem;
  }
}
</style>

