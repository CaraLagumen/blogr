<template>
  <div class="posts">
    <PostList :posts="loadedPosts"></PostList>
  </div>
</template>

<script>
import PostList from '~/components/Posts/PostList'

export default {
  components: { PostList },
  computed: {
    loadedPosts() {
      return this.$store.getters.loadedPosts
    },
  },
}
</script>

<style scoped></style>
