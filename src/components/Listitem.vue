<template>
  <div class="main" style>
    <div class="labels">
      <div v-for="(label) in translations" :key="getLabelKey(label)" class="listItem">
        <b>{{label[language] }}:</b>
      </div>
    </div>
    <div class="content">
      <div v-for="data in pcPartData" :key="getPartKey(data)">
        <b>{{data}}</b>
      </div>
    </div>
    <div class="cartButton">
      <span :class="[addedToCart ? 'aroundCartAfterClick' : 'aroundCart']" @click="handleClick">
        <div :class="[addedToCart ? 'fa-shopping-cart-color' : '', 'wrapperDiv']">
          <i :class="[ 'fas', 'fa-shopping-cart']"></i>
        </div>
      </span>
      <p v-if="addedToCart" style="margin-left: 3px">
        <b>Selected</b>
      </p>
    </div>
    <slot></slot>
  </div>
</template>
<script>
export default {
  name: "Listitem",
  data: function() {
    return { addedToCart: false, language: "ge" };
  },
  props: {
    pcPartData: Array,
    translations: Array,
    selectedItem: String
  },
  methods: {
    getLabelKey: function() {
      return Math.floor(Math.random() * 1000);
    },
    getPartKey: function() {
      return Math.floor(Math.random() * 1000);
    },
    handleClick: function() {
      this.addedToCart = !this.addedToCart;
      this.$emit("selected");
    }
  },

  mounted: function() {
    if (this.selectedItem == this.pcPartData[0]) {
      this.addedToCart = true;
    }
  }
};
</script>
<style>
.main {
  border-bottom: 2px solid grey;
  width: 70%;
  margin: auto;
  padding: 0 !important;
  display: grid;
  grid-template-columns: 5fr 1fr;
  grid-template-rows: 1fr 1fr;
  margin-top: 3rem;
}
.labels {
  height: 2rem;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem;
  grid-column: 1 / span 1;
  grid-row: 1/ 2;
}
.labels > * {
  flex-basis: 0;
  flex-grow: 1;
  border-left: 2px solid var(--tertiary);
}
.content {
  height: 2rem;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem;
  align-items: center;
  grid-column: 1 / 2;
  grid-row: 2/ 3;
}
.content > * {
  flex-basis: 0;
  flex-grow: 1;
  border-left: 2px solid var(--tertiary);
}
.wrapperDiv {
  display: inline-block;
}
.cartButton {
  width: 15%;
  display: flex;
  grid-column: 2 / 3;
  grid-row: 1 / 3;
  align-self: center;
  justify-self: center;
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
span {
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  -o-user-select: none;
  user-select: none;
}

@media screen and (min-width: 720px) {
  .main {
    padding: 0.5rem 5rem;
  }
}
</style>

