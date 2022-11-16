<template>
  <div id="app">
    <c-header />
    <c-page />
  </div>
</template>

<script>
import CHeader from './components/Header/Header.vue'
import CPage from './layouts/index.vue'

export default {
  name: 'App',

  components: {
    CPage,
    CHeader,
  }
}
</script>

<style lang="scss" src="./assets/Style.scss" />
