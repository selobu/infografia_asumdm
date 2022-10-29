<template>
  <v-container>
    <v-row>
      <v-col :cols="dosColumnas? '6':'12'">
        <v-hover v-slot="{ isHovering, props }">
          <v-card
            class="mx-auto"
            max-width="434"
            tile
            :elevation="isHovering ? 12 : 2"
            :class="{ 'on-hover': isHovering }"
            v-bind="props"
          >
            <div class="d-flex flex-no-wrap justify-space-between">
              <v-img
                height="100%"
                cover
                src="https://cdn.vuetifyjs.com/images/cards/server-room.jpg"
              >
                <v-avatar color="grey" size="150" rounded="0">
                  <v-img
                    cover
                    src="https://www.gravatar.com/avatar/302c652af1a74abdadf3dcaebd6513ee?s=250"
                    alt="Sebastian López"
                  ></v-img>
                </v-avatar>
                <v-list-item
                  class="text-white"
                  title="Sebastian López"
                  subtitle="Full Stack Developer"
                ></v-list-item>
              </v-img>
            </div>
            <v-card-actions>
              <v-row
                ><v-spacer></v-spacer
                ><v-switch
                  class="ma-2"
                  v-model="dosColumnas"
                  :label="
                    dosColumnas ? 'Mostrar dos columnas' : 'Mostrar una columna'
                  "
                  color="white"
                  hide-details
                ></v-switch
              ></v-row>
            </v-card-actions>
          </v-card>
        </v-hover>
      </v-col>
      <v-col :cols="dosColumnas? '6':'12'">
        <Card class="mx-auto"
          title="Metodología ASUM-DM"
          subtitle="Analítica de datos"
          :content="asumcontent"
          :image="asumimage"
        > </Card>
      </v-col>
    </v-row>
    <v-row class="text-center" v-if="showiniciar">
      <v-col
        ><v-btn
          color="blue-darken-3"
          append-icon="mdi-chevron-double-down"
          @click="showiniciar = false"
          >Inciar</v-btn
        ></v-col
      >
    </v-row>
    <v-row v-else max-width="900px">
      <v-col cols="12">
        <v-row>
          <v-spacer></v-spacer>
          <v-toolbar> </v-toolbar>
          <v-spacer></v-spacer
        ></v-row>
      </v-col>
      <v-col
        :cols="dosColumnas ? '6' : '12'"
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
          <template v-slot:nextbtn v-if="!item.desablenextbtn">
            <v-spacer></v-spacer>
            <v-btn
              class="ma-1"
              @click="changeview(index)"
              :icon="show ? 'mdi-chevron-up' : 'mdi-chevron-down'"
              variant="outlined"
              :color="show ? 'purple' : 'green'"
            ></v-btn>
            <v-spacer></v-spacer>
          </template>
        </Card>
      </v-col>
      <v-col cols="12">
        <v-row>
          <v-spacer></v-spacer
          ><v-btn
            icon="mdi-refresh"
            size="large"
            color="blue-darken-2"
            @click="onrefresh"
            title="Reiniciar"
            label="Reinciar"
          ></v-btn>
          <v-spacer></v-spacer>
        </v-row>
      </v-col>
    </v-row>
  </v-container>
  <Footer></Footer>
</template>

<script>
import Footer from "@/layout/Footer.vue";
import Card from "./card.vue";
export default {
  name: "HelloWorld",

  data: () => ({
    showPresentacion: false,
    showiniciar: true,
    dosColumnas: false,
    asumimage:"https://img.ibxk.com.br/2021/01/11/ibm-11183429805392.jpg?w=704",
    asumcontent:"Debido a las falencias en <strong>CRISP-DM</strong>, en 2015 IBM publicó el método unificado para\
            la solución de analíticas para el modelo de proceso de minado y predicción de datos - <strong>ASUM-DM</strong>.<br/>\
            Se basa en <strong>CRISP-DM</strong> per lo extiende con tareas y actividades en infraestructura, opercaciones, \
            proyecto y despliegue, tambien adiciona templates y guías a todas las tareas.<br/> \
            <strong>ASUM-DM</strong> hace parte de framework mas genéricollamado método unificado para la analítica de soluciones \
            <strong>ASUM </strong> que provee producto- y solucion - las rutas para la implementación específica\
            cubiendo todos los productos de analítica de <strong>IBM</strong>.",
    contents: {
      card1: {
        title: "Fase 1",
        subtitle: "Inicio del proyecto",
        image:
          "https://luisaolvera.com/wp-content/uploads/2019/06/a-que-edad-caminan-los-bebes-cuando-lo-hacen.jpg",
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
          "En esta etapa es importante entender: <br/><br/>\
          <ul> \
            <li> Cuales son esos objetivos,</li> \
            <li> Reconocer los requerimientos</li> \
            <li> LAs necesidade organizacionales</li> \
          </ul> \
          <br/> \
          Al identificar este aspecto se podrán reconocer aquellos\
          problemas que podrían resolverse con la implementación de la analítica\
        ",
      },
      card3: {
        title: "Fase 3",
        subtitle: "Descubrimiento y entendimiento de los datos",
        image: "https://miro.medium.com/max/3000/1*0o44SgYfO_NgbEbqRICftw.png",
        content:
          "Recolección inicial de datos para determinar la consistencia de la información:<br>\
         <ul>\
          <li>Fuente de datos: bases de datos, archivos csv, cluster</li>\
          <li>Compra de datos: a un tercero que recolecte datos</li>\
          <li>Datos abiertos: públicos que se puedan consultar</li>\
        </ul>",
      },
      card4: {
        title: "Fase 4",
        subtitle: "Preparación de los datos",
        image:
          "https://itcomunicacion.com.mx/wp-content/uploads/2020/02/datDeca-768x427.jpg",
        content:
          "<strong>Seleccionar los datos</strong>: Evitar traer los datos a la memoria en caso\
           del big data, por ejemplo en pyspark evitar convertir los datos a pandasdataframe\
           porque intenta llevarlos todos a la memoria<br/>\
           <strong>Filtrarlos:</strong> para buscar la información que se necesita o categorizarla<br/>\
           <strong>Completar:</strong> los datos que hagan falta<br/>\
           <strong>Integrar:</strong>los datos,<br/>\
           <strong>Homogenizar</strong>.",
      },
      card5: {
        title: "Fase 5",
        subtitle: "Construcción del modelo",
        image:
          "https://c5e6g5f8.rocketcdn.me/wp-content/uploads/2014/10/pexels-photo-534220.jpeg",
        content:
          "Escoger la técnica para realizar el modelo, diseñar pruebas, contruir el modelo",
      },
      card6: {
        title: "Fase 6",
        subtitle: "Evaluar el modelo",
        image: "https://miro.medium.com/max/1135/1*cwEeGqeSP5h5MXFm67lD3w.png",
        content:
          "Verificar si el resultado cumple con las metas del modelo y los objetivos del negocio,\
         sirve para realizar un mejor entendimiento de los datos de la empresa?<br/>\
         Los datos generan una nueva analítica?<br/>\
         Verificar si responde a las expectativas.<br/>\
         Rediseñar.",
      },
    },
    show: false,
  }),
  components: {
    Card,
    Footer,
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
