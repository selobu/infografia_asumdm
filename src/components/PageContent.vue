<template>
  <v-container>
    <v-row class="text-center" max-width="900px">
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
    <v-row class="text-center" v-if="showiniciar">
      <v-col
        ><v-btn
          color="primary"
          append-icon="mdi-chevron-down"
          @click="showiniciar = false"
          >Inciar</v-btn
        ></v-col
      >
    </v-row>
    <v-row v-else>
      <v-col cols="12" v-for="(item, index) in contents" :key="index">
        <Card
          v-if="item.showcurrent"
          :title="item.title"
          :image="item.image"
          :content="item.content"
          :subtitle="item.subtitle"
        >
          <template v-slot:nextbtn v-if="!item.desablenextbtn"
            ><v-btn
              @click="changeview(index)"
              variant="outlined"
              color="orange"
            >
              >>
            </v-btn>
          </template>
        </Card>
      </v-col>
      <v-col cols="6">
            <v-btn
              icon="mdi-refresh"
              size="large"
              color="primary"
              @click="onrefresh"
              title="Reiniciar"
              label="Reinciar"
            ></v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Card from "./card.vue";
export default {
  name: "HelloWorld",

  data: () => ({
    showPresentacion: false,
    showiniciar: true,
    contents: {
      card1: {
        title: "Fase 1",
        subtitle: "Inicio del proyecto",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "Lo primero es realizar un levantamiento de la información, \
          se debe hacer un diagnóstico respecto a qué tan preparada está la\
          compañía para iniciarse en un proyecto de analítica, dentro de esta\
          etapa se deben identificar factores como:\
          * Tecnologias\
          * Fuente de datos\
          * Acceso a la información\
          * Volumen\
          * Instalaciones\
        ",
        showcurrent: true,
        desablenextbtn: false,
      },
      card2: {
        title: "Fase 2",
        subtitle: "Enternder el negocio",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "En esta etapa es importante entender cuáles son esos objetivos,\
         pero, además, es fundamental reconocer los requerimientos y las necesidades\
         organizacionales, al identificar este aspecto se podrán reconocer aquellos\
         problemas que podrían resolverse con la implementación de la analítica",
        showcurrent: false,
        desablenextbtn: false,
      },
      card3: {
        title: "Fase 3",
        subtitle: "Descubrimiento y entendimiento de los datos",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "Recolección inicial de datos para determinar la consistencia de la información:\
         Fuente de datos, compra de datos, datos abiertos",
        showcurrent: false,
        desablenextbtn: false,
      },
      card4: {
        title: "Fase 4",
        subtitle: "Preparación de los datos",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "Seleccionar los datos, filtrarlos, completar los datos que haganfalta,\
         integración de los datos, homogenizar.",
        showcurrent: false,
        desablenextbtn: false,
      },
      card5: {
        title: "Fase 5",
        subtitle: "Construcción del modelo",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "Escoger la técnica para realizar el modelo, diseñar pruebas, controuir el modelo",
        showcurrent: false,
        desablenextbtn: false,
      },
      card6: {
        title: "Fase 6",
        subtitle: "Evaluar el modelo",
        image: "https://landmarkhunter.com/photos/57/54/575479-M.jpg",
        content: "Verificar si el resultado cumple con las metas del modelo,\
         sirve para realizar un mejor entendimiento de los datos de la empresa?\
         los datos generan una nueva analítica\
         verificar si responde a las expectativas.",
        showcurrent: false,
        desablenextbtn: false,
      },
    },
    show: false,
  }),
  components: {
    Card,
  },
  methods: {
    onrefresh() {
      this.showiniciar = true;
      let u = 1;
      const lencontents = Object.keys(this.contents).length;
      var newitems = { ...this.contents };
      for (const k in newitems) {
        newitems[k] = {
          ...newitems[k],
          showcurrent: u === 1 ? true : false,
          desablenextbtn: u === lencontents ? true : false,
        };
        u+=1;
      }
      this.contents = { ...newitems };
    },
    changeview(index) {
      var found = false;
      for (let k in this.contents) {
        if (found) {
          this.contents[k].showcurrent = true;
          break;
        }
        if (k === index) {
          this.contents[k].desablenextbtn = true;
          found = true;
        }
      }
    },
  },
};
</script>
