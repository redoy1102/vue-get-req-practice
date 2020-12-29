<template>
  <div>
    <h1>Blog article</h1>
    <div v-for="(blog,id) in blogs" :key="id">
      <h3>{{ blog.id }}</h3>
      <h2>{{ blog.title }}</h2>
      <p>{{ blog.body }}</p>
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      blogs: []
    }
  },
  created() {
    this.$http.get('https://jsonplaceholder.typicode.com/posts')
        .then((data) => {
          this.blogs = data.body.slice(0, 20)
        })
  }

}
</script>

<style scoped>

</style>