<script lang="ts">
import Vue from 'vue';
import VueNavbarCustomise from '@/vue-navbar-customise.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VueNavbarCustomise
  }
});
</script>

<template>
  <div id="app">
    <vue-navbar-customise />
  </div>
</template>
