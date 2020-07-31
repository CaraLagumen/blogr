<template>
  <button class="button" :class="btnStyle" v-bind="$attrs" v-on="$listeners">
    <slot />
  </button>
</template>

<script>
export default {
  name: 'AppButton',
  props: {
    btnStyle: {
      type: String,
      default: '',
    },
  },
}
</script>

<style scoped>
.button {
  padding: 0.5rem;
  border: 0.1rem solid black;

  background-color: black;
  color: white;
  font-size: 1.4rem;

  cursor: pointer;
}

.button:hover,
.button:active {
  border: 0.1rem solid black;
}

.inverted {
  background-color: white;
  color: black;
  border: 0.1rem solid transparent;
}

.inverted:hover,
.inverted:active {
  color: #ccc;
  background-color: white;
  border: 0.1rem solid transparent;
}

.cancel {
  background-color: red;
  color: white;
  border: 0.1rem solid transparent;
}

.cancel:hover,
.cancel:active {
  background-color: salmon;
  border: 0.1rem solid transparent;
  color: white;
}
</style>
