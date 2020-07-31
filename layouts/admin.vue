<template>
  <div>
    <Header @sidenavToggle="displaySidenav = !displaySidenav"></Header>
    <Sidenav :show="displaySidenav" @close="displaySidenav = false"></Sidenav>
    <Nuxt />
  </div>
</template>

<style></style>
