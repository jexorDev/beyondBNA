<script setup lang="ts">
    const props = defineProps<{
        type: number
    }>();
</script>
<template>

    <v-timeline side="end" truncate-line="both">
        <v-timeline-item dot-color="primary">
            <span>
            Follow signs marked <v-chip label color="success">Ground Transportation</v-chip> to level 1 of terminal
            </span>
        </v-timeline-item>
        <v-timeline-item dot-color="primary">
            <span>
            Exit terminal
            </span>
        </v-timeline-item>
        <v-timeline-item dot-color="primary">
            <span>
            Cross street to enter garage
            </span>
        </v-timeline-item>
        <v-timeline-item dot-color="primary">
            <span>
            Turn right to follow signs marked <v-chip label color="success">{{type === 0 ? "Shuttle" : "Bus"}}</v-chip> to next garage
            </span>
        </v-timeline-item>
        <v-timeline-item dot-color="primary" size="large">
             <template v-slot:icon>
                <v-icon icon="mdi-walk"></v-icon>
            </template>
            <span>2 min walk</span>
        </v-timeline-item>
          <v-timeline-item dot-color="black" size="large">
             <template v-slot:icon>
                <v-icon icon="mdi-flag-checkered"></v-icon>
            </template>
            <span>
            Use cross walk to get to <v-chip label color="success">{{type === 0 ? "Waiting Area 2" : "Area 4"}}</v-chip>
            </span>
        </v-timeline-item>
    </v-timeline>
</template>