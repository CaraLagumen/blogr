<template>
  <div class="admin">
    <section class="admin__new-post">
      <AppButton @click="$router.push('/admin/new-post')"
        >Create post</AppButton
      >
      <AppButton @click="onLogout">Logout</AppButton>
    </section>

    <section class="admin__existing-posts">
      <h1>Existing posts</h1>

      <PostList is-admin :posts="loadedPosts"></PostList>
    </section>
  </div>
</template>

<script>
import PostList from '~/components/Posts/PostList'
import AppButton from '~/components/UI/AppButton'

export default {
  layout: 'admin',
  middleware: ['check-auth', 'auth'],
  components: {
    PostList,
    AppButton,
  },
  computed: {
    loadedPosts() {
      return this.$store.getters.loadedPosts
    },
  },
  methods: {
    onLogout() {
      this.$store.dispatch('logout')
      this.$store.push('/admin/auth')
    },
  },
}
</script>

<style scoped>
.admin {
  padding: 2rem;
}

.admin__new-post {
  padding-bottom: 1rem;
  border-bottom: 0.2rem solid #ccc;

  text-align: center;
}

.admin__existing-posts h1 {
  text-align: center;
}
</style>
