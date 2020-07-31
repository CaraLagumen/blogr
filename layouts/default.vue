<template>
  <div>
    <Header @sidenavToggle="displaySidenav = !displaySidenav"></Header>
    <Sidenav :show="displaySidenav" @close="displaySidenav = false"></Sidenav>
    <Nuxt />
  </div>
</template>

<script>
import Header from '~/components/Navigation/Header'
import Sidenav from '~/components/Navigation/Sidenav'

export default {
  components: {
    Header,
    Sidenav,
  },
  data() {
    return {
      displaySidenav: false,
    }
  },
}
</script>

<style>
html {
  box-sizing: border-box;
  font-family: 'Open Sans', sans-serif;
  font-size: 62.5%;
}
body {
  font-family: var(--font-primary);
  color: black;

  font-weight: 400;
  line-height: 1.6;
}

a,
a:link,
a:visited {
  color: darkcyan;
  text-decoration: none;
}

ul {
  list-style-type: none;
}
</style>
