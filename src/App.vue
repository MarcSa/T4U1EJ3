<script setup lang="ts">
import Container from '@/components/Container.vue';
import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';
</script>

<template>
    <Header />
    <main class="content">
        <Container />
    </main>
    <Footer />
</template>

<style scoped>
main {
    background-color: #ebf0f1;
}
</style>
