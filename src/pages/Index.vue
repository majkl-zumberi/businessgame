<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <v-container fluid style="margin:0;padding:0" >
    <v-layout row justify-space-around class="first-section">
      <v-flex xs12 sm6 md5 class="pa-14">
        <span class="h5 font-weight-regular">ONLINE LEARNING</span>
          <h1 class="font-weight-regular">Learn <span class="font-weight-bold">Everyday</span></h1>
          <div class="text-wrapper-card">
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
          </div>
          <v-btn
            color="brown mt-9"
            dark >
            Normal Button
          </v-btn>
      </v-flex>
      <v-flex xs12 sm6 md7 class="image-container">
      </v-flex>
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
  height: 80vh;
  
}
.image-container{
  background-image: url("../assets/smiling-student-holding-books-and-feeling-confused.jpg"),linear-gradient(135deg, rgba(255,	224	,215	) 24%, rgba(255,	224,	215	) 84%);
  background-size: cover;
  width: 900px;
  height: auto;
  position: relative;
  /* mix-blend-mode: luminosity; */
  filter: hue-rotate(27deg);
  background-position: center;
  transform:scaleX(-1);
  border-radius: 5px;
  height: 80vh;
}
</style>
