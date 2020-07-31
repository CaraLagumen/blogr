<template>
  <div class="sidenav-container">
    <div v-if="show" class="sidenav-backdrop" @click="$emit('close')"></div>
    <transition name="slide-side">
      <div v-if="show" class="sidenav">
        <ul class="nav-list" @click="$emit('close')">
          <li class="nav-item"><nuxt-link to="/posts">Blog</nuxt-link></li>
          <li class="nav-item"><nuxt-link to="/about">About</nuxt-link></li>
          <li class="nav-item"><nuxt-link to="/admin">Admin</nuxt-link></li>
        </ul>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'Sidenav',
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style scoped>
.sidenav-container {
  height: 100%;
  width: 100%;
}

.sidenav-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 1000;

  height: 100%;
  width: 100%;

  background-color: rgba(0, 0, 0, 0.7);
}

.sidenav {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 10000;

  box-sizing: border-box;
  height: 100%;
  width: 30rem;
  padding: 3rem;

  background-color: white;
}

.slide-side-enter-active,
.slide-side-leave-active {
  transition: all 0.3s ease-out;
}
.slide-side-enter,
.slide-side-leave-to {
  transform: translateX(-100%);
}

.nav-list {
  margin: 0;
  padding: 0;
}

.nav-item {
  margin: 2rem 0;
}

.nav-item a {
  color: white;
  font-size: 2rem;
}
</style>
