<template>
  <v-container>
    <h1>Metronome</h1>
    <v-card class="mx-auto" max-width="600">
      <v-toolbar card dense>
        <v-toolbar-title>
          <span class="subheading">METRONOME</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn icon>
          <v-icon>mdi-share-variant</v-icon>
        </v-btn>
      </v-toolbar>

      <v-card-text>
        <v-layout justify-space-between mb-3>
          <v-flex text-xs-left>
            <span class="display-3 font-weight-light" v-text="bpm"></span>
            <span class="subheading font-weight-light mr-1">BPM</span>
            <v-fade-transition>
              <v-avatar
                v-if="isPlaying"
                :color="color"
                :style="{
                animationDuration: animationDuration
              }"
                class="mb-1 v-avatar--metronome"
                size="12"
              ></v-avatar>
            </v-fade-transition>
          </v-flex>
          <v-flex text-xs-right>
            <v-btn :color="color" dark depressed fab @click="toggle">
              <v-icon large>{{ isPlaying ? 'mdi-pause' : 'mdi-play' }}</v-icon>
            </v-btn>
          </v-flex>
        </v-layout>

        <v-slider v-model="bpm" :color="color" always-dirty min="40" max="218">
          <v-icon slot="prepend" :color="color" @click="decrement">mdi-minus</v-icon>

          <v-icon slot="append" :color="color" @click="increment">mdi-plus</v-icon>
        </v-slider>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    bpm: 40,
    interval: null,
    isPlaying: false
  }),

  computed: {
    color() {
      if (this.bpm < 100) return "indigo";
      if (this.bpm < 125) return "teal";
      if (this.bpm < 140) return "green";
      if (this.bpm < 175) return "orange";
      return "red";
    },
    animationDuration() {
      return `${60 / this.bpm}s`;
    }
  },

  methods: {
    decrement() {
      this.bpm--;
    },
    increment() {
      this.bpm++;
    },
    toggle() {
      this.isPlaying = !this.isPlaying;
    }
  }
};
</script>

<style>
@keyframes metronome-example {
  from {
    transform: scale(0.5);
  }

  to {
    transform: scale(1);
  }
}

.v-avatar--metronome {
  animation-name: metronome-example;
  animation-iteration-count: infinite;
  animation-direction: alternate;
}
</style>