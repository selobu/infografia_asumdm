<template>
  <v-app>
    <v-main>
      <HeaderToolbar />
      <PageContent />
      <Footer />
    </v-main>
  </v-app>
</template>

<script>
import PageContent from "./components/PageContent.vue";
import HeaderToolbar from "./layout/Toolbar.vue";
import Footer from '@/layout/Footer.vue';

export default {
  name: "App",

  components: {
    PageContent,
    HeaderToolbar,
    Footer,
  },

  data: () => ({
    //
  }),
};
</script>
