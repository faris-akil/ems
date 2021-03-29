<template>
  <div :style="setBackground">
    <v-row class="pa-5">
      <v-col
        v-for="theme in themes"
        :key="theme"
        class="d-flex child-flex"
        cols="3"
      >
        <v-card outlined class="pa-1" @click="setImageBackground(theme)">
          <v-img
            :src="theme"
            :lazy-src="theme"
            aspect-ratio="2"
            class="grey lighten-2"
          >
            <template v-slot:placeholder>
              <v-row class="fill-height ma-0" align="center" justify="center">
                <v-progress-circular
                  indeterminate
                  color="grey lighten-5"
                ></v-progress-circular>
              </v-row>
            </template>
          </v-img>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import field from "@/img/field.jpg";
import waves from "@/img/waves.jpg";

export default {
  data() {
    return {
      themes: [field, waves],
      choosen: "",
    };
  },
  computed: {
    setBackground() {
      return {
        background: `url(${this.choosen})`,
        height: "100vh",
      };
    },
  },
  methods: {
    setImageBackground(val) {
      this.choosen = val;
    },
  },
};
</script>

<style>
</style>