<script setup lang="ts">
import {onMounted} from "vue";
import HotelCard from './components/HotelCard.vue'
import hotels from "./data/hotels.json";

onMounted(() => {
 
  //console.log(JSON.parse(hotels))
  
})

</script>

<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row >
          <v-col v-for="hotel of hotels" cols="12" xs="12">
            <HotelCard :name="hotel.Name" :address="hotel.Address" :phone="hotel.Phone" :stars="hotel.Stars" :shuttleHours="hotel.ShuttleHours" :shuttleFrequency="hotel.ShuttleFrequency" :busStop="hotel.BusStop" :busStopDistance="hotel.BusStopDistance" :busStopTime="hotel.BusStopTime" />
          </v-col>
        </v-row>
        </v-container>  
    </v-main>
    </v-app>
</template>
