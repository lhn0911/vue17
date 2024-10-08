<template>
  <div>
    <h1>List product</h1>
    <input v-model="searchQuery" placeholder="Tìm kiếm theo tên" />
    <button @click="searchProduct">Tìm kiếm</button>

    <div v-if="filteredProducts.length">
      <div v-for="product in filteredProducts" :key="product.id">
        <img :src="product.image" alt="product.name" width="100" />
        <h3>{{ product.name }}</h3>
        <p>{{ product.price.toLocaleString() }} VND</p>
        <router-link :to="'/product-detail/' + product.id">
          <button>Xem chi tiết</button>
        </router-link>
      </div>
    </div>
    <div v-else>
      <p>Không có sản phẩm nào phù hợp với tìm kiếm</p>
    </div>
  </div>
</template>
  
  <script>
export default {
  data() {
    return {
      products: [
        {
          id: 1,
          name: "iPhone 15 Pro",
          price: 30000000,
          image: "https://example.com/images/iphone15pro.jpg",
        },
        {
          id: 2,
          name: "OPPO Reno11 5G",
          price: 10600000,
          image: "https://example.com/images/oppo_reno11.jpg",
        },
        {
          id: 3,
          name: "vivo Y17s",
          price: 3300000,
          image: "https://example.com/images/vivo_y17s.jpg",
        },
        {
          id: 4,
          name: "Samsung Galaxy S23 Ultra",
          price: 26000000,
          image: "https://example.com/images/samsung_s23ultra.jpg",
        },
        {
          id: 5,
          name: "Xiaomi 13T Pro",
          price: 17000000,
          image: "https://example.com/images/xiaomi_13tpro.jpg",
        },
      ],
      searchQuery: "",
      filteredProducts: [],
    };
  },
  mounted() {
    this.filterProductsByQuery();
  },
  methods: {
    searchProduct() {
      this.$router.push({
        path: "/list-product",
        query: { name: this.searchQuery },
      });
      this.filterProductsByQuery();
    },
    filterProductsByQuery() {
      const query = this.$route.query.name;
      if (query) {
        this.searchQuery = query;
        this.filteredProducts = this.products.filter((product) =>
          product.name.toLowerCase().includes(query.toLowerCase())
        );
      } else {
        this.filteredProducts = this.products;
      }
    },
  },
  watch: {
    "$route.query.name": "filterProductsByQuery",
  },
};
</script>
  
  <style scoped>
</style>
  