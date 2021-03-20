<template>
  <v-app class="layout">
    <v-app-bar app flat>
      <v-toolbar-title>Gridsome</v-toolbar-title>
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
</style>
