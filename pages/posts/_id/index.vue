<template>
  <div class="post">
    <section class="post__main">
      <h1 class="post__main--title">{{ loadedPost.title }}</h1>

      <div class="post__main--details">
        <div>Last updated on: {{ loadedPost.updatedDate }}</div>
        <div>Written by: {{ loadedPost.author }}</div>
      </div>

      <p>{{ loadedPost.content }}</p>
    </section>

    <section class="post__feedback">
      <p>Thoughts? Email me at <a>caralagumen@gmail.com</a>.</p>
    </section>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  asyncData(context) {
    if (context.payload) {
      return {
        loadedPost: context.payload.postData,
      }
    }

    return axios
      .get('https://blogrz.firebaseio.com/posts/' + context.params.id + '.json')
      .then((res) => {
        return {
          loadedPost: res.data,
        }
      })
      .catch((e) => context.error(e))
  },
}
</script>

<style scoped>
.post {
  padding: 3rem;

  text-align: center;
}

.post__main {
  width: 100%;
}

@media (min-width: 76.8rem) {
  .post__main {
    width: 60rem;
    margin: auto;
  }
}

.post__main--title {
  margin: 0;
}

.post__main--details {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  padding: 1rem;
  border-bottom: 0.3rem solid #ccc;
}

@media (min-width: 76.8rem) {
  .post__main--details {
    flex-direction: row;
  }
}

.post__main--details div {
  margin: 0 1rem;
}
</style>
