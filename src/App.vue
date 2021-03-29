<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        E.M.S v1
      </div>

      <v-spacer></v-spacer>

      <v-btn text to="/booking">
        <span class="mr-2">Booking</span>
        <v-icon>mdi-seat-outline</v-icon>
      </v-btn>
      <v-btn text to="/themes">
        <span class="mr-2">Themes</span>
        <v-icon>mdi-looks</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',



  data: () => ({
    //
  }),
};
</script>
