<script setup lang="ts">
import { ref } from 'vue';
const isShutterUp = ref<boolean>(true);
const shutterUpDown = () => {
    isShutterUp.value = !isShutterUp.value;
};
</script>

<template>
    <div class="col-12 col-sm-4 col-md-4">
        <div class="card h-100 mb-4">
            <div class="card-body">
                <div class="display-4 mb-1" @click="shutterUpDown">
                    <i class="bi bi-door-closed" v-if="!isShutterUp"></i>
                    <i class="bi bi-door-open" v-if="isShutterUp"></i>
                </div>
                <h3 class="mb-1">Persiana</h3>
                <p v-if="!isShutterUp" class="mb-3 lead">Cerrado</p>
                <p v-if="isShutterUp" class="mb-3 lead">Abierto</p>
                <div class="d-grid">
                    <button class="btn btn-secondary" @click="shutterUpDown">
                        <span v-if="!isShutterUp">Abrir</span>
                        <span v-if="isShutterUp">Cerrar</span>
                    </button>
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
</style>
