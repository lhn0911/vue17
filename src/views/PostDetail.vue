<template>
  <div>
    <h1>Chi Tiết Bài Viết</h1>
    <div v-if="post">
      <h2>{{ post.title }}</h2>
      <p>{{ post.content }}</p>
    </div>
    <div v-else>
      <p>Bài viết không tồn tại.</p>
    </div>
  </div>
</template>
  
  <script>
export default {
  data() {
    return {
      posts: [
        { id: 1, title: "Bài viết 1", content: "Nội dung bài viết 1." },
        { id: 2, title: "Bài viết 2", content: "Nội dung bài viết 2." },
        { id: 3, title: "Bài viết 3", content: "Nội dung bài viết 3." },
      ],
    };
  },
  computed: {
    post() {
      return this.posts.find(
        (post) => post.id === parseInt(this.$route.params.id)
      );
    },
  },
};
</script>
  