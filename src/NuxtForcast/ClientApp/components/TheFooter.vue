<template>
  <footer class="footer fixed-bottom">
    <b-container> &copy; {{ year }} - Levin Joller </b-container>
  </footer>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  data() {
    return {
      year: new Date().getFullYear(),
    }
  },
})
</script>

<style>
.footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 60px;
  line-height: 60px;
  background-color: #f5f5f5;
}
</style>
