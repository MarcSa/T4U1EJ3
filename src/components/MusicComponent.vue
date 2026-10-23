<script setup lang="ts">
import { ref } from 'vue';
const isMusicPlaying = ref<boolean>(false);
const musicPlayStop = () => {
    isMusicPlaying.value = !isMusicPlaying.value;
};
</script>

<template>
    <div class="col-12 col-sm-4 col-md-4">
        <div class="card h-100 mb-4">
            <div class="card-body">
                <div class="display-4 mb-1" @click="musicPlayStop">
                    <i class="bi bi-play-fill" v-if="!isMusicPlaying"></i>
                    <i class="bi bi-pause-fill" v-if="isMusicPlaying"></i>
                </div>
                <h3 class="mb-2">Música</h3>
                <p v-if="!isMusicPlaying" class="mb-3 lead">Pausado</p>
                <p v-if="isMusicPlaying" class="mb-3 lead">Reproduciendo</p>
                <button class="btn btn-secondary mb-1 me-2" @click="musicPlayStop">
                    <span v-if="!isMusicPlaying">Reproducir</span>
                    <span v-if="isMusicPlaying">Pausar</span>
                </button>
                <button class="btn btn-secondary mb-1 me-2">Siguiente</button>
            </div>
        </div>
    </div>
</template>

<style scoped type="scss">
.card {
    -webkit-box-shadow: 0px 0px 6px 0px #616161;
    box-shadow: 0px 0px 6px 0px #616161;
    border: none;
}
</style>
