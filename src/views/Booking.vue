<template>
  <div class="my-2 text-center pa-4">
    <div class="rectangle mb-3">
      <div class="rectangle-text">Stage</div>
    </div>
    <div>
      <v-btn @click="proceedToBook">Save</v-btn>
    </div>
    <div class="d-flex justify-center mb-6 pa-3 flex-wrap">
      <template v-for="item in seats">
        <v-card
          v-if="!item.hasOwnProperty('booked')"
          outlined
          class="pa-2 ma-2"
          dark
          :color="item.taken ? 'green darken-1' : 'grey darken-1'"
          :key="item.id"
          @click="item.taken = !item.taken"
        >
          <template>
            <v-icon>mdi-seat</v-icon>
            <div class="my-1">
              {{ item.id }}
            </div>
          </template>
        </v-card>
        <v-card
          v-else
          outlined
          class="pa-2 ma-2"
          :key="item.id"
          color="red lighten-1"
          disabled
        >
          <template>
            <v-icon>mdi-seat</v-icon>
            <div class="my-1">
              {{ item.id }}
            </div>
          </template>
        </v-card>
      </template>

      <!-- 
              COLOR MATERIAL:
                1. green darken-1
                2. red darken-1
           -->
      <!-- <v-card outlined class="pa-2">Area 2</v-card>
          <v-card outlined class="pa-2">Area 3</v-card> -->
    </div>
    <v-dialog
      v-model="dialog"
      max-width="290"
    >
      <v-card>
        <v-card-title class="headline">
          Seats Booked !!
        </v-card-title>

        <v-card-text>
          Congratulations. Your seat has been booked for the event. We hope to see you very soon.
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="green darken-1"
            text
            @click="dialog = false"
          >
            OKAY
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
import seats from "@/data/seats.js";

export default {
  data() {
    return {
      seats: seats,
      dialog: false,
    };
  },
  methods: {
      proceedToBook(){
          this.seats = this.seats.map(seat => seat.taken ? {...seat, booked: true,} : seat )
          this.dialog = true
      }
  }
};
</script>

<style scoped>
.rectangle {
  display: flex;
  height: 300px;
  margin: auto;
  max-width: 800px;
  border: 1px solid black;
  justify-content: center;
  align-items: center;
}
.rectangle-text {
  font-size: 2rem;
  /* content: 'stage' */
}
.seats {
  display: flex;
}
.areas {
  border: 1px solid black;
}
</style>