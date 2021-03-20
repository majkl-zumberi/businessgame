<template>
  <Layout>

    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <v-container fluid style="margin:0;padding:0" >
    <v-layout row justify-space-around class=" first-section">
      <v-flex xs12 sm5 md5 class="pa-14">
        <h1>ONLINE LEARNING</h1>
          <h2>Learn Everyday</h2>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
      </v-flex>
      <v-flex xs12 sm7 md7 class="image-container">
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
.home-links a {
  margin-right: 1rem;
}
.first-section{
   background: rgb(255,	224,	215);
  background: linear-gradient(135deg, rgba(255,	224,	215) 24%, rgba(255,	224,	215) 84%); 
  height: 75vh;
  
}
.image-container{
  background-image: url("../assets/smiling-student-holding-books-and-feeling-confused.jpg"),linear-gradient(135deg, rgba(255,	224	,215	) 24%, rgba(255,	224,	215	) 84%);
  background-size: cover;
  width: 900px;
  height: auto;
  position: relative;
  mix-blend-mode: luminosity;
  background-position: center;
  transform:scaleX(-1);
  border-radius: 5px;
  height: 75vh;
}
</style>
