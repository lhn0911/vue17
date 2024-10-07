<template>
  <div>
    <h1>Tìm kiếm</h1>
    <input
      v-model="keyword"
      type="text"
      placeholder="Nhập từ khóa tìm kiếm..."
    />
    <button @click="search">Tìm kiếm</button>

    <div v-if="query">
      <p>
        Value: <strong>{{ query }}</strong>
      </p>
    </div>
  </div>
</template>
  
  <script>
export default {
  data() {
    return {
      keyword: "",
    };
  },
  computed: {
    query() {
      return this.$route.query.q;
    },
  },
  methods: {
    search() {
      if (this.keyword) {
        this.$router.push({ path: "/search", query: { q: this.keyword } });
      }
    },
  },
};
</script>
  