<template>
  <section class="posts-list">
    <PostPreview
      v-for="post in posts"
      :id="post.id"
      :key="post.id"
      :is-admin="isAdmin"
      :title="post.title"
      :preview-text="post.previewText"
      :thumbnail="post.thumbnail"
    ></PostPreview>
  </section>
</template>

<script>
import PostPreview from '~/components/Posts/PostPreview'

export default {
  components: { PostPreview },
  props: {
    isAdmin: {
      type: Boolean,
      default: false,
    },
    posts: {
      type: Array,
      required: true,
    },
  },
}
</script>

<style scoped>
.posts-list {
  display: grid;
  align-items: center;
  justify-content: center;
  gap: 2rem;

  padding: 2rem;
}
</style>
