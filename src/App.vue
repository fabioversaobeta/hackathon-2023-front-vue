<template>
  <div class="background">
    <div id="app">
      <div>
        <ClusterPage />
      </div>
    </div>
</div>
</template>

<script>
import ClusterPage from '@/pages/ClusterPage.vue';

export default {
  name: 'App',
  components: {
    ClusterPage,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background-color: #2c3e50;
  color: #2c3e50;
  padding: 40px;
  overflow-y: scroll;
}
</style>
