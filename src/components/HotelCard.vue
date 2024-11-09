<script setup lang="ts">
import {ref, computed} from "vue";

const props = defineProps<{
    name: string;
    address: string;
    phone: string;
    stars: number;
    shuttleHours: string;
    shuttleFrequency: string;        
}>();

const phone = computed(() => `tel:+1-${props.phone}`);
const selectedTransportType = ref<number>(0);

</script>

<template>
  <v-card>
      
    <v-card-title>
        {{props.name}}
    </v-card-title>
    <v-card-subtitle>
        <div>
            {{props.address}}
        </div>
        
        <div>
        <v-rating
  :length="5"
  :size="20"
  :model-value="props.stars"
  active-color="warning"
  class="mt-2"
 />
    <div class="font-italic">{{props.stars}} Star Hotel</div>
    </div>
    </v-card-subtitle>
        <v-divider/>
    <v-card-text>
        <div class="text-overline">Transportation</div>
        <v-chip-group mandatory v-model="selectedTransportType">            
            <v-chip color="primary" size="small">Complimentary Shuttle</v-chip>
            <v-chip color="orange" size="small">Taxi</v-chip>
            <v-chip color="black" size="small">Uber</v-chip>
            <v-chip color="pink" size="small">Lyft</v-chip>
        </v-chip-group>

        <v-row>
            <v-col>
                <div class="text-overline">Available</div>
        <div>{{shuttleHours}}</div>
            </v-col>
            <v-col>
                <div class="text-overline">Frequency</div>
        <div>{{shuttleFrequency}}</div>
            </v-col>
        </v-row>
        <v-row>
            <v-col>                
                <div class="text-overline">Pick up at</div>
                <div>Ground Transportation Center - Waiting Area 2</div>
                <v-btn size="small" color="success" class="mt-2"> <v-icon icon="mdi-map-marker-path" start></v-icon> Guide me there</v-btn>
            </v-col>
        </v-row>

    </v-card-text>
    <v-divider/>
    <v-card-actions>
        <v-btn color="primary"><v-icon icon="mdi-phone" start ></v-icon><a :href="phone">Call</a></v-btn>
    </v-card-actions>
    </v-card>
</template>
