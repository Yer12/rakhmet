<template>
  <div class="quantity" :class="(count===0)?'noItem':''">
    <button @click="decreaseQty" class="inc_item" :class="(count===0)?'nodisplay':''">
      -
    </button>
    <p v-if="count!==0">{{count}}</p>
    <button @click="increaseQty" class="dec_item">
      +
    </button>
  </div>
</template>

<script>
export default {
  name: "QuantityButton",
  props: {
    product: {
      type: Object
    },
    productQty: {
      type: Number
    }
  },
  data() {
    return {
      count: this.productQty,
      qtyUpdatedButton: 0,
      // cartProduct: {
      //   p_id: this.product.product_id,
      //   p_title: this.product.product_name,
      //   p_price: this.product.p_price,
      //   p_img: this.product.p_img,
      // }
    }
  },
  methods: {
    increaseQty() {
      this.count += 1;
      this.$emit('countUpdated', this.product.price);
      this.$store.dispatch("addProductToCart", {p: this.product, c: this.count})
    },
    decreaseQty() {
      if(this.count >0) {
        this.count -=1
      }
      this.qtyUpdatedButton =  this.count
      this.$emit('countUpdated', -this.product.price);
      this.$store.dispatch("removeProductToCart", {p: this.product, c: this.count})
    }
  }
}
</script>

<style scoped>
.nodisplay {
  display: none !important;
}
.noItem {
  background: transparent !important;
}
.add_item {
  position: absolute;
  bottom: 4px;
  right: 4px;
  background: #FFFFFF;
  border: none;
  width: 36px;
  height: 35px;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: 1px 2px 10px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  font-weight: 500;
  font-size: 22px;
  color: #2997FF;
}
.product_without_img .quantity {
  right: 18px;
}
.quantity {
  border-radius: 8px;
  box-shadow: 1px 2px 10px rgba(0, 0, 0, 0.1);
  display: flex;
  position: absolute;
  align-items: center;
  font-weight: normal;
  font-size: 16px;
  color: #131113;
  bottom: 4px;
  right: 4px;
  background: #FFFFFF;
}
.quantity p {
  margin: 0;
  padding: 0;
}
.dec_item, .inc_item {
  border: none;
  background: #FFFFFF;
  width: 36px;
  height: 35px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 4px;
  font-weight: 500;
  font-size: 18px;
  color: #2997FF;
}
</style>
