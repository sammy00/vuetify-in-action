<template>
  <v-layout row wrap>
    <v-flex sm12>
      <h1>Editable Steps</h1>
    </v-flex>
    <v-flex sm12>
      <v-stepper>
        <v-stepper-header>
          <v-stepper-step complete editable step="1">Select campaign settings</v-stepper-step>

          <v-divider></v-divider>

          <v-stepper-step complete step="2">Create an ad group</v-stepper-step>

          <v-divider></v-divider>

          <v-stepper-step step="3">Create an ad</v-stepper-step>
        </v-stepper-header>
      </v-stepper>
    </v-flex>
  </v-layout>
</template>