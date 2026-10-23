<script setup lang="ts">
import RoomSection from '@/components/RoomSection.vue';
import EVehicleComponent from '@/components/EVehicleComponent.vue';
import LastChargeComponent from '@/components/LastChargeComponent.vue';
import LightsComponet from '@/components/LightsComponet.vue';
import MusicComponent from '@/components/MusicComponent.vue';
import ShuttersComponent from '@/components/ShuttersComponent.vue';
</script>

<template>
    <div class="container pt-4">
        <div class="row">
            <div class="col col-12 mb-3"><h1>Panel de control</h1></div>
        </div>
        <div class="habitacion mb-4">
            <h2>Habitación</h2>
            <RoomSection>
                <LightsComponet />
                <ShuttersComponent />
                <MusicComponent />
            </RoomSection>
        </div>
        <div class="coche">
            <h2>Coche eléctrico</h2>

            <RoomSection>
                <EVehicleComponent />
                <LastChargeComponent />
            </RoomSection>
        </div>
    </div>
</template>

<style scoped></style>
