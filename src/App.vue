<script setup lang="ts">
import {onMounted} from "vue";
import HotelCard from './components/HotelCard.vue'
import HotelModel from "./models/HotelModel";
import hotels from "./data/hotels.json";

onMounted(() => {
 
  //console.log(JSON.parse(hotels))
  
})

</script>

<template>
<v-layout :fluid="true">
  <v-main>
    <v-row>
      <v-col v-for="hotel of hotels">
        <HotelCard :name="hotel.Name" :address="hotel.Address" :phone="hotel.Phone" :stars="hotel.Stars" :shuttleHours="hotel.ShuttleHours" shuttleFrequency="On Demand (must call)" />
      </v-col>
    </v-row>
    </v-main>
    </v-layout>
</template>
