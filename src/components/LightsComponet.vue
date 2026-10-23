<script setup lang="ts">
import { ref } from 'vue';
const brightness = ref<number>(50);
const areLightsOn = ref<boolean>(false);
const lightsOnOff = () => {
    areLightsOn.value = !areLightsOn.value;

    if (areLightsOn.value && brightness.value === 0) {
        brightness.value = 50;
    }
};
const handleBrightness = () => {
    if (brightness.value === 0) {
        areLightsOn.value = false;
    }
};
</script>

<template>
    <div class="col-12 col-sm-4 col-md-4">
        <div class="card h-100 mb-4">
            <div class="card-body">
                <div class="display-4 mb-1" @click="lightsOnOff">
                    <i class="bi bi-lightbulb-off" v-if="!areLightsOn"></i>
                    <i class="bi bi-lightbulb" v-if="areLightsOn"></i>
                </div>
                <h3 class="mb-2">Luces</h3>
                <button v-if="!areLightsOn" class="button" @click="lightsOnOff">Encender</button>
                <input
                    type="range"
                    id="brightness"
                    name="brightness"
                    min="0"
                    max="100"
                    v-model.number="brightness"
                    v-if="areLightsOn"
                    @input="handleBrightness"
                />
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    -webkit-box-shadow: 0px 0px 6px 0px #616161;
    box-shadow: 0px 0px 6px 0px #616161;
    border: none;
}
.button {
    background: #ffffff;
    border: none;
    padding: 0;
}
</style>
