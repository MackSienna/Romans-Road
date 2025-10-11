<script setup>
import Grid from '../Grid.vue'
import { templeHealthFacts } from '../../utils';
const props = defineProps({
    handleSelectWorkout: Function,
    firstIncompleteWorkoutIndex: Number
})

const randomNumber = Math.floor(Math.random() * templeHealthFacts.length)
const todaysTip = templeHealthFacts[randomNumber]

</script>

<template>
    <section id="dashboard">
        <div class="card tip-container">
            <h2>Welcome, Soldier</h2>
            <div>
                <p class="tip"><strong>Daily word</strong> <i>Verbum Cotidianum
</i><br/>{{ todaysTip }}</p>
            </div>
            <button @click="() => handleSelectWorkout(firstIncompleteWorkoutIndex < 0 ? 0 : 
            firstIncompleteWorkoutIndex)
                ">Start Regiment &rarr; </button>
    </div>
    <Grid v-bind="props" />

    </section>
</template>

<style scoped>
    .tip-container,
    .tip-container div,
    #dashboard {
        display: flex;

    }
    .tip-container,
    #dashboard {
        flex-direction: column;

    }
    #dashboard {
        gap: 2rem;
    }
    .tip-container {
        gap: 0.4rem;
    }

    
    @media (min-width: 560px) {
    tip-container {
        gap: 2rem;
        padding: 2.1rem 0;
    }

    .benefits {
        gap: 0.5rem;
    }
}


</style>
