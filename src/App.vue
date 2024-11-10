<script setup lang="ts">
import {onMounted} from "vue";
import HotelCard from './components/HotelCard.vue'
import hotels from "./data/hotels.json";

onMounted(() => {
 
  //console.log(JSON.parse(hotels))
  
})

</script>

<template>
<v-layout>
  <v-main>
    <v-row v-for="hotel of hotels">
      <v-col>
        <HotelCard :name="hotel.Name" :address="hotel.Address" :phone="hotel.Phone" :stars="hotel.Stars" :shuttleHours="hotel.ShuttleHours" :shuttleFrequency="hotel.ShuttleFrequency" :busStop="hotel.BusStop" :busStopDistance="hotel.BusStopDistance" :busStopTime="hotel.BusStopTime" />
      </v-col>
    </v-row>
    </v-main>
    </v-layout>
</template>
