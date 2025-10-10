<script setup>
    import { ref } from 'vue'
    import Vestibulum from '../Vestibulum.vue';
    import { workoutProgram, exerciseDescriptions } from '../../utils';
    const selectedWorkout = 4
    const { workout, warmup } = workoutProgram[selectedWorkout]
    let selectedExercise = ref(null)
    console.log(selectedExercise)
    const exerciseDescription = exerciseDescriptions[selectedExercise]

    function handleCloseModal () {
        selectedExercise.value = null
    }
</script>

<template>
    <Vestibulum v-if="selectedExercise">
     <div class="exercise-description">
        <h4>{{ selectedExercise }}</h4>
     <div>
        <small>Description</small>
        <p>{{ exerciseDescription }}</p>
    </div>
        <button @click="handleCloseModal">Understood <i class="fa-solid fa-spell-check"></i></button>
     </div>  
      </Vestibulum>
    <section id="workout-card">
        <div class="plan-card card">
            <div class="plan-card-header">
                <p>Day {{ selectedWorkout < 9 ? '0' + selectedWorkout : selectedWorkout }}
                    </p>
                  <i class="fa-solid fa-person-walking"></i>
                </div>
                <h2>{{ 'Ruck' }} Workout </h2>
            </div>
                <div class="workout-grid">
                <h4 class="grid-name">Warmup</h4>
                <h7>Duration</h7>
                <h7>Ratio</h7>
                <h6 class="grid-equipment">Equipment</h6>
                    <div class="workout-grid-row" v-for="(w, wIdx) in warmup" :key="wIdx">
                      <div class="grid-name">
                        <p>{{ w.name }}</p>
                        <button @click="() => {
                            selectedExercise.value = w.name
                        }">
                            <i class="fa-solid fa-circle-info"></i>
                            </button>
                        </div>
                        <p>{{ w.sets }}</p>
                        <p>{{ w.reps }}</p>
                        <input class="grid-equipment" placeholder="Backpack" type="text" disabled/>
                    </div>
                    <div class="workout-grid-line"></div>
                    <h4 class="grid-name">Workout</h4>
                <h7>Duration</h7>
                <h7>Ratio</h7>
                <h6 class="grid-equipment">Equipment</h6>
                       <div class="workout-grid-row" v-for="(w, wIdx) in workout" :key="wIdx">
                      <div class="grid-name">
                        <p>{{ w.name }}</p>
                        <button @click="() => {
                            selectedExercise.value = w.name
                        }">
                        <i class="fa-solid fa-circle-info"></i>
                            </button>
                        </div>
                        <p>{{ w.sets }}</p>
                        <p>{{ w.reps }}</p>
                        <input class="grid-equipment" placeholder="Any Backpack" type="text" />
                    </div>
                </div>
                <div class="card workout-btns">
                    <button>Log & Exit <i class="fa-solid fa-feather-pointed"></i></button>
                    <button>Advance <i class="fa-solid fa-arrow-right-to-bracket"></i></button>
                    </div>
        </section>
</template>

<style scoped>
#workout-card,
.plan-card {
    display: flex;
    flex-direction: column;

}

#workout-card {
    gap: 1.5rem;
}

.plan-card-header,
.workout-btns {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 0.4rem;
}
 
.workout-grid,
.workout-grid-row {
    display: grid;
    grid-template-columns: repeat(7, minmax(0, 1fr));
    gap: 1rem;

}

.workout-grid-row,
.workout-grid-line {
    grid-column: span 7 / span 7;
}

.grid-name {
    grid-column: span 3 / span 3;
    display: flex;
    align-items: center;
    gap: 1rem;
}

.grid-name button {
    padding: 0;
    border: none;
    box-shadow: 2px 3px #888888;
}

.grid-name button:hover{
    transform: none;
    box-shadow: none;
    color: var(--color-link);
}

.workout-grid-row .grid-name button {
    opacity: 0;
    pointer-events: none;
}

.workout-grid-row:hover .grid-name button {
    opacity: 1;
    pointer-events: all;
}

.grid-name p {
    text-transform: capitalize;
}

.grid-equipement {
    grid-column: span 2 / span 2;
}

.workout-btns button {
    flex: 1;
}

.workout-btns button i {
    gap: 0.7rem;
}

.exercise-description {
    display: flex;
    flex-direction: column;
    gap: 1rem;
}

.exercise-description button i {
    padding-left: 0.110rem;

}
</style>
