<script setup>
import Layout from './components/layouts/Layout.vue';
import Tecum from './components/pages/Tecum.vue';
import Taberna from './components/pages/Taberna.vue';
import Disciplina from './components/pages/Disciplina.vue'

const selectedDisplay = 2



</script>

<template>
    <Layout>
    <!-- [PAGE 1] -->
    <Tecum v-if="selectedDisplay == 1" />
    <!-- [PAGE 2] -->
    <Taberna v-if="selectedDisplay == 2"/>
    <!-- [PAGE 3] -->
     <Disciplina v-if="selectedDisplay == 3"/>

    </Layout>
</template>

<style scoped>
 
</style>
