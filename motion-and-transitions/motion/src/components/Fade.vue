<template>
  <div class="text-xs-center">
    <v-menu transition="fade-transition">
      <v-btn slot="activator" dark color="primary">Fade Transition</v-btn>
      <v-list>
        <v-list-tile v-for="n in 5" :key="n">
          <v-list-tile-title v-text="'Item ' + n"></v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-menu>
  </div>
</template>