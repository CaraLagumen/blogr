<template>
  <div class="post">
    <section class="post__update">
      <AdminPostForm :post="loadedPost" @submit="onSubmitted"></AdminPostForm>
    </section>
  </div>
</template>

<script>
import axios from 'axios'

import AdminPostForm from '~/components/Admin/AdminPostForm'

export default {
  layout: 'admin',
  middleware: ['check-auth', 'auth'],
  components: {
    AdminPostForm,
  },
  asyncData(context) {
    return axios
      .get(
        'https://blogrz.firebaseio.com/posts/' + context.params.postId + '.json'
      )
      .then((res) => {
        return {
          loadedPost: { ...res.data, id: context.params.postId },
        }
      })
      .catch((e) => context.error())
  },
  methods: {
    onSubmitted(editedPost) {
      this.$store.dispatch('editPost', editedPost).then(() => {
        this.$router.push('/admin')
      })
    },
  },
}
</script>

<style scoped>
.post__update {
  display: grid;
  align-content: center;
  justify-content: center;

  width: 70vw;
  margin: 2rem auto;
}

@media (min-width: 76.8rem) {
  .post__update {
    width: 50rem;
  }
}
</style>
