<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <v-container fluid style="margin:0;padding:0;ovewflow-x:hidden;" >
    <v-layout row justify-space-around class="first-section">
      <v-flex xs12 sm6 md5 justify-center class="pa-14 pa-md-16" style="background: inherit;">
        <div class="d-lg-flex flex-lg-column align-lg-center" style="height:31.25em;">
          <span class="h5 font-weight-regular">ONLINE LEARNING</span>
          <h1 class="font-weight-regular">Learn <span class="font-weight-bold">Everyday</span></h1>
          <div class="text-wrapper-card">
            <p class="font-weight-bold">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
          </div>
          <v-btn
            color="brown mt-9"
            dark >
            Normal Button
          </v-btn>
        </div>
      </v-flex>
      <v-flex xs12 sm6 md7 class="image-container">
        <div></div>
      </v-flex>
      <v-row no-gutters class="pa-14 pa-md-16">
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
            <p class="text-h6 text-md-h5 headline blue-grey--text text--darken-3 font-weight-light">Get access to high quality learning!</p>
            <h1 class="font-weight-regular text-h4 text-md-h3">Join online courses <span class="font-weight-bold">today</span></h1>
            <p class="text-wrapper-card font-weight-bold">Etiam velit purus, vehicula quis imperdiet dignissim, convallis vitae nisl. Nullam facilisi. Pellentesque non pulvinar justo. Nullam eget neque ut tellus ornare ullamcorper ulla ambco mattis for nulla glavrida egesed!</p>
            <v-btn
              color="brown mt-9"
              dark >
              Read more
            </v-btn>
          </div>
        </v-col>
      </v-row >

      <v-row no-gutters align="center" class="pa-14 pa-md-16" style="background-color:#ffe0d7;">
        <v-col cols="12"  xs="12" sm="9" md="4" lg="3" offset-sm="3" offset-md="2" offset-lg="3">
          <h1 class="font-weight-regular ">Train Your Brain Today!</h1>
          <p class="text-wrapper-card">Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in ​reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.</p>
           <v-btn
            class="px-2 mb-sm-2 mb-2"
            outlined
            color="brown"
            :width="$vuetify.breakpoint.xs?'100%':null"
          >
            All courses
          </v-btn>
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
      
    </v-layout>
    
    </v-container>
 
    

  </Layout>
</template>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
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
  position: relative;
  /* mix-blend-mode: luminosity; */
  filter: hue-rotate(27deg);
  background-position: top center;
  transform:scaleX(-1);
  border-radius: 5px;
  height: 70vh;
}
</style>
