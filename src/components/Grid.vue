<script setup>
import { workoutProgram } from "../utils";
const workoutTypes = ["Ruck", "Functional Strength", "Full - Body"];
defineProps({
  handleSelectWorkout: Function,
  firstIncompleteWorkoutIndex: Number,
  handleResetPlan: Function,
});
</script>

<template>
  <section id="grid">
    <button
      :disabled="workoutIdx > 0 && workoutIdx > firstIncompleteWorkoutIndex"
      @click="() => handleSelectWorkout(workoutIdx)"
      :key="workoutIdx"
      v-for="(workout, workoutIdx) in Object.keys(workoutProgram)"
      class="card-button plan-card"
    >
      <div>
        <p>
          Day {{ workoutIdx < 9 ? "0" + (workoutIdx + 1) : workoutIdx + 1 }}
        </p>
        <i class="fa-solid fa-person-walking" v-if="workoutIdx % 3 == 0"></i>
        <i class="fa-solid fa-dumbbell" v-if="workoutIdx % 3 == 1"></i>
        <i class="fa-solid fa-gears" v-if="workoutIdx % 3 == 2"></i>
      </div>
      <h3>{{ workoutTypes[workoutIdx % 3] }}</h3>
    </button>
    <button
      :disabled="firstIncompleteWorkoutIndex != -1"
      @click="handleResetPlan"
      class="card-button plan-card-reset"
    >
      <p>Renew</p>
    </button>
  </section>
</template>

<style scoped>
#grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1rem;
}
#grid button {
  width: 100%;
}
#grid button:disabled {
  box-shadow: none;
  cursor: not-allowed;
}
.plan-card {
  display: flex;
  flex-direction: column;
}

.plan.plan-card-reset {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.8rem;
}

.plan-card div {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.5rem;
}

.plan-card div p {
  text-align: left;
}

@media (min-width: 560px) {
  #grid {
    grid-template-columns: repeat(4, minmax(1, 1fr));
  }
}
</style>
