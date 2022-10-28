<template>
  <v-card class="mx-auto" max-width="500px">
    <v-img :src="image" height="200px" cover></v-img>
    <v-card-title>{{ title }}</v-card-title>
    <v-card-subtitle>{{ subtitle }}</v-card-subtitle>

    <v-card-actions>
      <slot name="nextbtn"></slot>
      <v-spacer></v-spacer>

      <v-btn
        @click="show = !show"
        :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
        variant="outlined"
        color="green"
      ></v-btn>
    </v-card-actions>
    <v-card-text v-if="show">{{ content }}</v-card-text>blier
  </v-card>
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