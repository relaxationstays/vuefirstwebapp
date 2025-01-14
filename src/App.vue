<template>
  <HeaderPage />
  <ReleasePage />
</template>
<script>

import HeaderPage from './views/Header/HeaderPage.vue';
import ReleasePage from './views/Release/ReleasePage.vue';

export default {
  name: 'App',
  components: {
    HeaderPage,
    ReleasePage
  },
  mounted() {
    document.title = 'Musiki';
  },
};
</script>
<style scoped>
body {
  font-optical-sizing: auto;
  font-weight: 500;
  font-style: normal;
  font-family: "Montserrat", serif !important;
}
</style>
