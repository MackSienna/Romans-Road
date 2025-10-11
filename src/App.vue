<script setup>
import Layout from './components/layouts/Layout.vue';
import Tecum from './components/pages/Tecum.vue';
import Taberna from './components/pages/Taberna.vue';
import Disciplina from './components/pages/Disciplina.vue'
import { computed, ref } from 'vue';
import { workoutProgram } from './utils';

const defaultData = {}
for (let workoutIdx in workoutProgram) {
    const workoutData = workoutProgram[workoutIdx]
    defaultData[workoutIdx] = {}
    for (let e of workoutData.workout)
        defaultData[workoutIdx][e.name] = ''
}
const selectedDisplay = ref(1)
const data = ref(defaultData)
const selectedWorkout = ref(-1)

const isWorkoutComplete = computed(() => {
    const currWorkout = data.value?.[selectedWorkout.value]
    if (!currWorkout) { return false } 
    const isCompleteCheck =  Object.values(currWorkout).every(ex => !!ex)
console.log('ISCOMPLETE: ', isCompleteCheck)
return isCompleteCheck
})

const firstIncompleteWorkoutIndex = computed(()=> {
    const allWorkouts = data.value
    if (!allWorkouts) { return -1 }
    for (const [index, workout] of Object.entries(allWorkouts)) {
        const isComplete = Object.values(workout).every(ex => !!ex)
        if (!isComplete) {
            return parseInt(index)
        }
    }
    return -1 // com
})

function handleChangeDisplay(idx) {
    selectedDisplay.value = idx
}
function handleSelectWorkout(idx) {
    selectedDisplay.value = 3
    selectedWorkout.value = idx
}
function handleSaveWorkout() {
    localStorage.setItem('workouts', JSON.stringify(data.value))
    selectedDisplay.value = 2
    selectedWorkout.value = -1
}




</script>

<template>
    <Layout>
    <!-- [PAGE 1] -->
    <Tecum :handleChangeDisplay="handleChangeDisplay" v-if="selectedDisplay == 1" />
    <!-- [PAGE 2] -->
    <Taberna :firstIncompleteWorkoutIndex="firstIncompleteWorkoutIndex" :handleSelectWorkout="handleSelectWorkout" v-if="selectedDisplay == 2"/>
    <!-- [PAGE 3] -->
     <Disciplina :handleSaveWorkout="handleSaveWorkout"  :isWorkoutComplete="isWorkoutComplete" :data="data" :selectedWorkout="selectedWorkout" v-if="workoutProgram?.[selectedWorkout]"/>

    </Layout>
</template>

<style scoped>
 
</style>
