<template>
    <v-footer class="bg-blue-lighten-1 text-center d-flex flex-column"
  >
    <div class="pt-0">
      Infografía.
    </div>

    <v-divider></v-divider>

    <div>
      {{ new Date().getFullYear() }} — <strong>Sebastian López Buriticá</strong>
    </div></v-footer>
</template>
<script>
export default {
    name: 'Footer'    
}
</script>