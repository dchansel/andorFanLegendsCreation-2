<script setup>
import { ref,defineProps } from 'vue';

const props = defineProps({
    legend: {
        type: Object,
        default: () => ({})
    }
});

const legend = ref(props.legend);
</script>

<template>
    <v-row>
        <v-col cols="3" class="sm-4" align-self="end">
            <v-radio-group v-model="legend.type" inline hide-details class="small">
                <v-radio v-bind:label="$t('standaloneLegend')" value="single" name="unique"></v-radio>
                <v-radio v-bind:label="$t('sagaLegend')" value="series" name="saga"></v-radio>
            </v-radio-group>
        </v-col>
        <v-col cols="3" class="sm-4" v-if="(legend.type === 'series')">
            <v-text-field
                v-if="(legend.type === 'series')"
                v-bind:label="$t('sagaName')"
                v-model="legend.series"
                variant="underlined"
                required
                hide-details
            ></v-text-field>
        </v-col>
        <v-col cols="2" v-if="(legend.type === 'series')">
            <v-text-field
                v-if="(legend.type === 'series')"
                v-bind:label="$t('sagaNumber')"
                v-model="legend.number"
                variant="underlined"
                required
                hide-details
            ></v-text-field>
        </v-col>
        <v-col>
            <v-text-field
                v-bind:label="$t('legendTitle')"
                variant="underlined"
                v-model="legend.name"
                required
                hide-details
            ></v-text-field>
        </v-col>
    </v-row>
</template>