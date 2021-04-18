<template>
  <Layout>
    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <v-container fluid style="margin:0;padding:0;" >
    <v-layout row justify-space-around class="first-section">
      <v-flex xs12 sm6 md5 justify-center class="pa-14 pa-md-16" style="background: inherit;">
        <div class="d-lg-flex flex-lg-column align-lg-center" style="height:31.25em;">
          <span class="h5 font-weight-regular">ONLINE LEARNING</span>
          <h1 class="font-weight-regular mb-md-12">Learn <span class="font-weight-bold">Everyday</span></h1>
          <div class="text-wrapper-card">
            <p class="font-weight-bold">Scopri cosa significa essere un vero Marketer attraverso i nostri corsi dedicati al mondo marketing! <br> Ti aspettiamo!</p>
          </div>
          <g-link to="/survey/">
            <v-btn
              color="brown mt-9"
              dark >
              Candidati
            </v-btn>
          </g-link>
        </div>
      </v-flex>
      <v-flex xs12 sm6 md7 class="image-container">
        <div></div>
      </v-flex>
      <v-row no-gutters class="pa-14 pa-md-16 white">
        <v-col cols="12" xs="12" sm="10" md="3" xl="2" offset-sm="2" offset-md="2" offset-xl="3" >
          <section class="pa-3">
            <div class="image-circle-container">
              
              <img 
              class="image-circle"
              :style="$vuetify.breakpoint.xs?'object-position: left center;':null"
              :width="$vuetify.breakpoint.xs?'300px':$vuetify.breakpoint.sm?'350px':'417px'"
              :height="$vuetify.breakpoint.xs?'300px':$vuetify.breakpoint.sm?'350px':'417px'"
              src="../assets/image-of-beautiful-cheerful-girl-with-toothy-smile-writes-notes-in-notebook-with-pencil.jpg"/>
          </div>
        </section>    
        </v-col>
        <v-col cols="12" xs="12" sm="12" md="5" xl="6" offset-md="2" offset-xl="1" class="pa-6 pa-md-16">
          <div class="image-circle-container">
            <p class="text-h6 text-md-h5 headline blue-grey--text text--darken-3 font-weight-light">Ottieni l'accesso ad un apprendimento di alta qualità!</p>
            <h1 class="font-weight-regular text-h4 text-md-h3">Iscriviti ai corsi online <span class="font-weight-bold">oggi</span></h1>
            <p class="mt-2 text-wrapper-card font-weight-bold">Sviluppa nuove competenze per un mondo digitale, scopri gli aspetti fondamentali del marketing digitale grazie ai nostri corsi tutti creati da formatori Professionisti</p>
             <v-btn
            class="px-2 mb-sm-2 mb-2"
            outlined
            color="brown"
            :width="$vuetify.breakpoint.xs?'100%':null"
          >
            Scopri tutti i corsi
          </v-btn>
          </div>
        </v-col>
      </v-row >

      <v-row no-gutters align="center" class="pa-14 pa-md-16" style="background-color:#ffe0d7;">
        <v-col cols="12"  xs="12" sm="9" md="4" lg="3" offset-sm="3" offset-md="2" offset-lg="3">
          <h1 class="font-weight-regular ">Mettiti alla prova!</h1>
          <p class="text-wrapper-card">Testa la tua digital marketing knowledge eseguendo un semplice quiz</p>
           <g-link to="/quiz/">
            <v-btn
              class="px-2 mb-sm-2 mb-2"
              outlined
              color="brown"
              :width="$vuetify.breakpoint.xs?'100%':null"
            >
              avvia quiz
            </v-btn>
          </g-link>
           
        </v-col>

        <v-col cols="12" xs="12" sm="9" md="4" lg="3" offset-sm="3" offset-md="2" offset-lg="0" >
          <img 
          class="image-circle"
          :style="$vuetify.breakpoint.xs?'object-position: right center;':null"
          :width="$vuetify.breakpoint.xs?'300px':$vuetify.breakpoint.sm?'320px':'417px'"
          :height="$vuetify.breakpoint.xs?'300px':$vuetify.breakpoint.sm?'320px':'417px'"
          src="../assets/adult-smiling-casual-clothes-guy-with-beard-hugs-favorite-books-to-himself-isolated-on-pink.jpg"/>
        </v-col>
      </v-row>
      <v-row  class="pa-14 pa-md-16 white">
        <v-col cols="12"  xs="12" sm="12" md="12" lg="12">
          <h1 class=" text-center font-weight-regular">Ecco alcuni corsi che offriamo:</h1>
        </v-col>
        <v-card
            v-for="edge in $page.courses.edges" :key="edge.node.id"
            class="mx-auto mt-5"
            width="300"
            >
            <v-img
                class="white--text align-end"
                height="200px"
                :src="edge.node.image"
                >
            </v-img>
            <v-card-title class="brown--text">{{edge.node.title}}</v-card-title>
            <v-card-subtitle>
              {{edge.node.description}}
            </v-card-subtitle>
            
            
          </v-card>
      </v-row >
      <v-footer
    dark
    padless
  >
    <v-card
      flat
      tile
      class="brown lighten-3 black--text text-center"
    >
      <v-card-text>
        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4 white--text"
          icon
        >
          <v-icon size="24px">
            {{ icon }}
          </v-icon>
        </v-btn>
      </v-card-text>

      <v-card-text class="white--text pt-0">
        Talenti4Future nasce per assecondare il desiderio di ognuno di essere protagonista e per stimolarti a fare della tua vita qualcosa di grande. È proprio il desiderio ciò che prendiamo a cuore all’inizio del tuo percorso, ancor prima delle tue competenze, per aiutarti a raggiungere i tuoi obiettivi personali, accademici e professionali.
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        {{ new Date().getFullYear() }} — <strong>TALENTI4FUTURE</strong>
      </v-card-text>
    </v-card>
  </v-footer>
    </v-layout>
    
    </v-container>
 
    

  </Layout>
</template>
<page-query>
query{
  courses: allCourse {
    edges {
      node {
        id
        title
        description
        image
      }
    }
  }
}
</page-query>
<script>
export default {
  metaInfo: {
    title: 'Homepage'
  },
  data(){
    return {
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
    }
  }
}
</script>

<style>
.row + .row {
    margin: 0 !important;
}
.circle{
  border-radius: 50%;

}
.image-circle{
  /* width: 26.6875em;
  height: 26.6875em; */
  border-radius: 50%;
  object-fit: cover; 
  object-position:  center;
  background-position: center;
  position: relative; 
  resize: both;
  -webkit-box-shadow: 29px 40px 0px 0px rgba(255,	224,	215);
-moz-box-shadow: 29px 40px 0px 0px rgba(255,	224,	215);
box-shadow: 29px 40px 0px 0px rgba(255,	224,	215); 
}
.image-circle-container{
   position: relative; 
}
.circle{
   position: absolute; 

  left: 50px;
  bottom: -50px;
  z-index: 0;
  width: 26.6875em;
  height: 26.6875em;
  border-radius: 50%;
  background: #c1a29a;
}
.text-wrapper-card{
  padding: 1em 2em;
  line-height: 2rem;
  max-width: 20rem;
  min-width: 15rem;
  background-color: #c1a29a;
  border-radius: 10px;
  color: white;
  text-align: left;
}
h1,h5{
  font-size: 3.4rem;
}
h1,h2,p,span{
  font-family: "nunito";
}
.home-links a {
  margin-right: 1rem;
}
.first-section{
   background: rgb(255,	224,	215);
  background: linear-gradient(135deg, rgba(255,	224,	215) 24%, rgba(255,	224,	215) 84%); 
  height: 70vh;
  
}
.image-container{
  background-image: url("../assets/smiling-student-holding-books-and-feeling-confused.jpg"),linear-gradient(135deg, rgba(255,	224	,215	) 24%, rgba(255,	224,	215	) 84%);
  background-size: cover;
  width: 900px;
  height: auto;
  min-height:70vh;
  position: relative;
  /* mix-blend-mode: luminosity; */
  filter: hue-rotate(27deg);
  background-position: top center;
  transform:scaleX(-1);
  border-radius: 5px;
}
</style>
