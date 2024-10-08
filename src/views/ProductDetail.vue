<template>
  <div>
    <h1>Product Detail</h1>
    <div v-if="product">
      <img :src="product.image" alt="product.name" width="200" />
      <p>Id: {{ product.id }}</p>
      <p>ProductName: {{ product.name }}</p>
      <p>Price: {{ product.price.toLocaleString() }} VND</p>
    </div>
    <div v-else>
      <p>Không tìm thấy sản phẩm</p>
    </div>
  </div>
</template>
  
  <script>
export default {
  data() {
    return {
      product: null,
    };
  },
  mounted() {
    const productId = this.$route.params.id;
    const products = JSON.parse(localStorage.getItem("products"));
    if (products) {
      this.product = products.find((p) => p.id === parseInt(productId));
    }
  },
};
</script>
  
  <style scoped>
</style>
  