<script setup lang="ts">
import {ref, computed} from "vue";
import GuideTimeline from "./GuideTimeline.vue";

const props = defineProps<{
    name: string;
    address: string;
    phone: string;
    stars: number;
    shuttleHours: string;
    shuttleFrequency: string;    
    busStop: string;
    busStopDistance: string;
    busStopTime: string;    
}>();

const phone = computed(() => `tel:+1-${props.phone}`);
const selectedTransportType = ref(0);
const showGuideTimeline = ref(false);

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
  readonly
 />
    <div class="font-italic">{{props.stars}} Star Hotel</div>
    </div>
    </v-card-subtitle>
        <v-divider/>
    <v-card-text>
        <div class="text-overline">Transportation Options</div>
        <v-chip-group mandatory v-model="selectedTransportType">            
            <v-chip v-show="shuttleHours" color="primary" size="small">Complimentary Shuttle</v-chip>
            <v-chip color="orange" size="small">Taxi</v-chip>
            <v-chip color="black" size="small">Uber</v-chip>
            <v-chip color="pink" size="small">Lyft</v-chip>
            <v-chip v-show="busStop" color="purple" size="small">Bus</v-chip>
        </v-chip-group>

        <div v-show="shuttleHours && selectedTransportType === 0">

            <v-row>
                <v-col>
                    <div class="text-overline">Available</div>
            <div>{{shuttleHours}}</div>
                </v-col>
                <v-col>
                    <div class="text-overline">Frequency</div>
            <div>{{shuttleFrequency === "" ? "On Demand (Must call)" : `Every ${shuttleFrequency} min`}}</div>
                </v-col>
            </v-row>
            <v-row>
                <v-col>                
                    <div class="text-overline">Pick up at</div>
                    <div>Ground Transportation Center - Waiting Area 2</div>
                    <v-btn @click="showGuideTimeline = true" size="small" color="success" class="mt-2"> <v-icon icon="mdi-map-marker-path" start ></v-icon> Guide me there</v-btn>
                </v-col>
            </v-row>
           
        </div>
        <div v-show="busStop && selectedTransportType === 4">
            <v-row>
                <v-col>
                    <div class="text-overline">Bus Stop</div>
            <div>{{busStop}}</div>
            <v-btn size="small" color="primary" class="mt-2"> <v-icon icon="mdi-information-variant" start ></v-icon> Bus Info</v-btn>
                </v-col>
            </v-row>
            <v-row>
                <v-col>
                    <div class="text-overline">Walk distance</div>
            <div>{{busStopDistance}} feet</div>
                </v-col>
                <v-col>                
                    <div class="text-overline">Walk duration</div>
                    <div>{{busStopTime}} minutes</div>
                </v-col>
            </v-row>
             <v-row>
                <v-col>
                    <div class="text-overline">Pick up at</div>
                    <div>Ground Transportation Center - Area 4</div>
                    <v-btn @click="showGuideTimeline = true" size="small" color="success" class="mt-2"> <v-icon icon="mdi-map-marker-path" start ></v-icon> Guide me there</v-btn>
                </v-col>
            </v-row>
        </div>

    </v-card-text>
    <v-divider/>
    <v-card-actions>
        <v-btn color="primary"><v-icon icon="mdi-phone" start ></v-icon><a :href="phone">Call</a></v-btn>
    </v-card-actions>
    </v-card>
    <v-dialog v-model="showGuideTimeline" fullscreen>
        <v-card>
            <v-card-title>
                <v-icon icon="mdi-close" @click="showGuideTimeline = false"></v-icon>
            </v-card-title>
            <v-card-text>
                <GuideTimeline :type="selectedTransportType"></GuideTimeline>
            </v-card-text>
        
        </v-card>
    </v-dialog>
</template>
