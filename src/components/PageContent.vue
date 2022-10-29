<template>
  <v-container>
    <v-row class="text-center" max-width="900px">
      <v-col cols="12">
        <v-avatar>
          <v-img
            src="https://www.gravatar.com/avatar/302c652af1a74abdadf3dcaebd6513ee?s=250"
            alt="Sebastian López"
          ></v-img>
        </v-avatar>
      </v-col>
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">INFOGRAFÍA ASUM-DM</h1>
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
    <v-row v-else max-width="900px">
      <v-col cols="12">
        <v-row>
          <v-spacer></v-spacer>
          <v-switch
            v-model="dosColumnas"
            :label="dosColumnas ? 'Dos columnas' : 'Una columna'"
          ></v-switch>
          <v-spacer></v-spacer
        ></v-row>
      </v-col>
      <v-col :cols="dosColumnas? '6':'12'" v-for="(item, index) in contents" :key="index">
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
    dosColumnas: false,
    contents: {
      card1: {
        title: "Fase 1",
        subtitle: "Inicio del proyecto",
        image:
          "https://2.bp.blogspot.com/-FRa4mAipzcA/Vf8gYlkPa8I/AAAAAAAAAg0/IMAUboWhtJo/s1600/INICIO.png",
        content:
          "Lo primero es realizar un levantamiento de la información, \
          se debe hacer un diagnóstico respecto a qué tan preparada está la\
          compañía para iniciarse en un proyecto de analítica, dentro de esta\
          etapa se deben identificar factores como:<br/><br/>\
          <ul>\
            <li>Tecnologias.</li>\
            <li>Fuente de datos</li>\
            <li>Acceso a la información</li>\
            <li>Volumen</li>\
            <li>Instalaciones</li>\
          </ul>\
        ",
      },
      card2: {
        title: "Fase 2",
        subtitle: "Enternder el negocio",
        image:
          "https://agenciadomus.com.mx/blog/wp-content/uploads/2019/06/blog-e1560797059757-1140x641.jpg",
        content:
          "En esta etapa es importante entender cuáles son esos objetivos,\
         pero, además, es fundamental reconocer los requerimientos y las necesidades\
         organizacionales, al identificar este aspecto se podrán reconocer aquellos\
         problemas que podrían resolverse con la implementación de la analítica",
      },
      card3: {
        title: "Fase 3",
        subtitle: "Descubrimiento y entendimiento de los datos",
        image: "https://miro.medium.com/max/3000/1*0o44SgYfO_NgbEbqRICftw.png",
        content:
          "Recolección inicial de datos para determinar la consistencia de la información:\
         Fuente de datos, compra de datos, datos abiertos",
      },
      card4: {
        title: "Fase 4",
        subtitle: "Preparación de los datos",
        image:
          "https://itcomunicacion.com.mx/wp-content/uploads/2020/02/datDeca-768x427.jpg",
        content:
          "Seleccionar los datos, filtrarlos, completar los datos que hagan falta,\
         integración de los datos, homogenizar.",
      },
      card5: {
        title: "Fase 5",
        subtitle: "Construcción del modelo",
        image:
          "https://c5e6g5f8.rocketcdn.me/wp-content/uploads/2014/10/pexels-photo-534220.jpeg",
        content:
          "Escoger la técnica para realizar el modelo, diseñar pruebas, controuir el modelo",
      },
      card6: {
        title: "Fase 6",
        subtitle: "Evaluar el modelo",
        image: "https://miro.medium.com/max/1135/1*cwEeGqeSP5h5MXFm67lD3w.png",
        content:
          "Verificar si el resultado cumple con las metas del modelo,\
         sirve para realizar un mejor entendimiento de los datos de la empresa?\
         los datos generan una nueva analítica\
         verificar si responde a las expectativas.",
      },
    },
    show: false,
  }),
  components: {
    Card,
  },
  beforeMount() {
    this.contents = this.f_restarcontents(this.contents);
  },
  methods: {
    f_restarcontents(contents) {
      let u = 1;
      const lencontents = Object.keys(contents).length;
      var newitems = { ...contents };
      for (const k in newitems) {
        newitems[k] = {
          ...newitems[k],
          showcurrent: u === 1 ? true : false,
          desablenextbtn: u === lencontents ? true : false,
        };
        u += 1;
      }
      return { ...newitems };
    },
    onrefresh() {
      this.showiniciar = true;
      this.contents = this.f_restarcontents(this.contents);
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
