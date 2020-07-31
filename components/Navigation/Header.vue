<template>
  <div class="header-container">
    <header class="header">
      <SideNavToggle @toggle="$emit('sidenavToggle')" />
      <div class="logo">
        <nuxt-link to="/">BLOGR</nuxt-link>
      </div>
      <div class="spacer"></div>
      <div class="navigation-items">
        <ul class="nav-list">
          <li class="nav-item"><nuxt-link to="/posts">Blog</nuxt-link></li>
          <li class="nav-item"><nuxt-link to="/about">About</nuxt-link></li>
          <li class="nav-item"><nuxt-link to="/admin">Admin</nuxt-link></li>
        </ul>
      </div>
    </header>
  </div>
</template>

<script>
import SideNavToggle from '~/components/Navigation/SideNavToggle'

export default {
  name: 'Header',
  components: {
    SideNavToggle,
  },
}
</script>

<style scoped>
.header-container {
  height: 6rem;
}

.header {
  display: flex;
  align-items: center;
  justify-content: space-around;
  position: fixed;
  z-index: 100;

  height: 6rem;
  padding: 0 2rem;

  background-color: darkcyan;
}

.logo {
  margin: 0 1rem;
  font-size: 4rem;
}

.logo a {
  color: white;
}

.spacer {
  flex: 1;
}

.navigation-items {
  display: none;
}

@media (min-width: 76.8rem) {
  .navigation-items {
    display: block;
  }
}

.nav-list {
  display: flex;

  margin: 0;
  padding: 0;

  font-size: 2rem;
}

.nav-item {
  margin: 0 1rem;
}

.nav-item a {
  color: white;
}

.nav-item a:hover,
.nav-item a:active,
.nav-item a.nuxt-link-active {
  color: white;
}
</style>
