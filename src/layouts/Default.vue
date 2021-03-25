<template>
  <v-app class="layout">
    <v-app-bar app flat class="brown lighten-2">
      <v-toolbar-title class="white--text">Talenti4Future</v-toolbar-title>
    </v-app-bar>
    <v-main>
      <slot/>
    </v-main>
  </v-app>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style>
.layout{
  width: auto;
}
html,body{ overflow-x: hidden; }
</style>
