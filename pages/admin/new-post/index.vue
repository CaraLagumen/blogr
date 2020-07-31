<template>
  <div class="post">
    <section class="post__new">
      <AdminPostForm @submit="onSubmitted"></AdminPostForm>
    </section>
  </div>
</template>

<script>
import AdminPostForm from '~/components/Admin/AdminPostForm'

export default {
  layout: 'admin',
  middleware: ['check-auth', 'auth'],
  components: {
    AdminPostForm,
  },
  methods: {
    onSubmitted(post) {
      this.$store
        .dispatch('addPost', post)
        .then(() => this.$router.push('/admin'))
    },
  },
}
</script>

<style scoped>
.post__new {
  width: 90%;
  margin: 20px auto;
}

@media (min-width: 768px) {
  .post__new {
    width: 500px;
  }
}
</style>
