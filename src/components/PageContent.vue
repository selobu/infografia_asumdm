<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          src="https://gestionhseq.com/assets/img/Logotipo.svg"
          class="my-2"
          contain
          height="50"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          BIENVENIDO A LA INFOGRAFÍA
        </h1>
      </v-col>
    </v-row>
    <v-row >
      <v-col
        cols="6"
        v-for="(item, index) in contents"
        :key="index"
      >
        <Card 
          v-if="item.showcurrent"
          :title="item.title"
          :image="item.image"
          :content="item.content"
          :subtitle="item.subtitle"
        >
        <template v-slot:nextbtn v-if="!item.desablenextbtn"><v-btn
          @click="changeview(index)"
        variant="outlined"
         color="orange">siguiente >>
        </v-btn>
        </template>
      
      </Card>
        <v-container></v-container>
      </v-col>
    </v-row>
    <v-row>
      <v-container>
        <v-btn prepend-icon="mdi-refresh" size="x-large" color="green" @click="onrefresh">Rerfrescar</v-btn>
      </v-container>
    </v-row>
  </v-container>
</template>

<script>
import Card from "./card.vue";
export default {
  name: "HelloWorld",

  data: () => ({
    contents: {
      card1: {
        title: "uno",
        subtitle: "subtitle",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "lorem ipsum",
        showcurrent: true,
        desablenextbtn: false
      },
      card2: {
        title: "dos",
        subtitle: "subtitle",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "lorem ipsum",
        showcurrent: false,
        desablenextbtn: false,
      },
      card3: {
        title: "tres",
        subtitle: "subtitle",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "lorem ipsum",
        showcurrent: false,
        desablenextbtn: false
      },
    },
    show: false,
  }),
  components: {
    Card,
  },
  methods: {
    onrefresh() {
      var u = 1;
      for (let k in this.contents) { 
        this.contents[k] = {
          ...this.contents[k], showcurrent:
            u === 1 ? true : false,
          desablenextbtn: false
        }
        u++
      }
    },
    changeview(index) {
      console.log({ index })
      var found = false;
      for (let k in this.contents) { 
        console.log(k)
        if (found) {
          this.contents[k].showcurrent = true 
          break
        }
        if (k === index) { 
          this.contents[k].desablenextbtn = true
          found = true
        }
      }
     }
  }
};
</script>
