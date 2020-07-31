<template>
  <nuxt-link :to="postLink" class="posts-preview">
    <article>
      <div
        class="posts-preview__thumbnail"
        :style="{ backgroundImage: `url('${thumbnail}')` }"
      ></div>
      <div class="posts-preview__content">
        <h1>{{ title }}</h1>
        <p>{{ previewText }}</p>
      </div>
    </article>
  </nuxt-link>
</template>

<script>
export default {
  name: 'PostPreview',
  props: {
    isAdmin: { type: Boolean, required: true },
    id: { type: String, required: true },
    title: { type: String, required: true },
    previewText: { type: String, required: true },
    thumbnail: { type: String, required: true },
  },
  computed: {
    postLink() {
      return this.isAdmin ? '/admin/' + this.id : '/posts/' + this.id
    },
  },
}
</script>

<style>
.posts-preview {
  width: 70vw;
  border: 0.1rem solid #ccc;
  box-shadow: 0 0.2rem 0.2rem #ccc;

  background-color: white;
}

a {
  color: white;
  background-color: darkcyan;
}

.posts-preview__thumbnail {
  height: 20rem;
  background-position: center;
  background-size: cover;
}

.posts-preview__content {
  padding: 1rem;
  text-align: center;
}

a:hover .posts-preview__content,
a:active .posts-preview__content {
  background-color: #ccc;
}

h1 {
  font-size: 2.5rem;
}

p {
  font-size: 2rem;
}
</style>
