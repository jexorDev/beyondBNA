<script setup lang="ts">
import HotelCard from './HotelCard.vue'
import hotels from "../data/hotels.json";
import {computed, ref} from "vue";

const selectedHotelAddress = ref<string | null>(null)

const filteredHotels = computed(() => selectedHotelAddress.value  ? hotels.filter(x => x.Address === selectedHotelAddress.value) : hotels)

</script>
<template>
  <v-container>
    <v-row>
        <v-autocomplete :items="hotels" item-title="Name" item-value="Address" v-model="selectedHotelAddress" clearable variant="outlined" prepend-inner-icon="mdi-magnify"></v-autocomplete>
        
    </v-row>
        <v-row >
          <v-col v-for="hotel of filteredHotels">
            <HotelCard :name="hotel.Name" :address="hotel.Address" :phone="hotel.Phone" :stars="hotel.Stars" :shuttleHours="hotel.ShuttleHours" :shuttleFrequency="hotel.ShuttleFrequency" :busStop="hotel.BusStop" :busStopDistance="hotel.BusStopDistance" :busStopTime="hotel.BusStopTime" />
          </v-col>
        </v-row>
        </v-container>  
    </template>