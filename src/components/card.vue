<template>
  <v-hover open-delay="100">
  <template v-slot:default="{  isHovering, props }">
    <v-card class="mx-auto" max-width="500px"  
    :elevation="isHovering ? 12 : 2"
    v-bind="props">
      <v-img :src="image" height="200px" cover></v-img>

      <v-card-title>{{ title }}</v-card-title>
      <v-card-subtitle>{{ subtitle }}</v-card-subtitle>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn
          @click="show = !show"
          :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
          variant="outlined"
          :color="show ? 'purple' : 'green'"
        ></v-btn>
        <v-spacer></v-spacer>
      </v-card-actions>
      <v-card-text v-if="show"
        ><p v-html="content"></p>
        <br />
        <br />
        <v-row> <v-spacer></v-spacer><slot name="nextbtn"></slot></v-row>
      </v-card-text>
    </v-card>
  </template>
  </v-hover>
</template>
<script>
export default {
  props: {
    title: { type: String, required: true },
    subtitle: { type: String, required: false, default: "----" },
    content: { type: String, required: true },
    image: {
      type: String,
      required: false,
      default: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
    },
  },
  data: () => ({
    show: false,
  }),
};
</script>
