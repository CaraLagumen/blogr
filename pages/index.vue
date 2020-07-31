<template>
  <div class="home">
    <section class="home__intro">
      <h1>My journey with Vue</h1>
    </section>

    <section class="home__posts">
      <PostList :posts="loadedPosts"></PostList>
    </section>
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

<style scoped>
.home__intro {
  position: relative;

  height: 20rem;
  padding: 3rem;

  background-image: url('~assets/images/mountain.jpg');
  background-position: center;
  background-size: cover;
}

.home__intro h1 {
  padding: 2rem;

  color: white;
  font-size: 3rem;
}

@media (min-width: 76.8rem) {
  .home h1 {
    font-size: 2rem;
  }
}

.home__posts {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;

  padding: 2rem;
}
</style>
