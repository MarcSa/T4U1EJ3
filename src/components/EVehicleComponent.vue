<script setup lang="ts">
import { ref } from 'vue';
const charge = ref<number>(45);
const isCharging = ref<boolean>(false);
const timeout: number = 150;

const time = () => {
    charge.value = charge.value + 1;
    if (charge.value > 99) return '';
    setTimeout(time, timeout);
};
const chargeOnOff = () => {
    isCharging.value = !isCharging.value;
    setTimeout(time, 1);
};
</script>

<template>
    <div class="col-12 col-sm-4 col-md-4 mb-4">
        <div class="card h-100">
            <div class="card-body">
                <div class="display-4 mb-1">
                    <i class="bi bi-car-front-fill"></i>
                </div>
                <h3 class="mb-2">Vehículo eléctrico</h3>
                <p v-if="!isCharging" class="mb-3 lead">Desconectado</p>
                <p v-if="isCharging" class="mb-3 lead">Cargando</p>

                <div class="d-grid">
                    <button
                        class="btn btn-secondary mb-2"
                        @click="chargeOnOff"
                        :disabled="isCharging"
                    >
                        <span v-if="!isCharging">Conectar</span>
                        <span v-if="isCharging">Desconectar</span>
                    </button>
                </div>
                <div class="progress">
                    <div
                        class="progress-bar"
                        role="progressbar"
                        :style="{ width: `${charge}%` }"
                        aria-valuenow="25"
                        aria-valuemin="0"
                        aria-valuemax="100"
                    >
                        {{ charge }}
                    </div>
                </div>
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
