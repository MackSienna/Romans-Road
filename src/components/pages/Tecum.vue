<script setup>
</script>

<template>
    <section id="welcome">
    <div class="benefits">
     <h2>Complete this ratio</h2>
     <div>
         <p>✅ Sequere Viam Lucis, become disciplined. <strong>Train Like Legionaries</strong> </p>
            <p><i>Crucifige Carnem — Esto Templum Dei</i></p>
    </div>
    </div>
    <div>
        <h3>Regiment</h3>
        <p>A hybrid endurance and strength system inspired by the physical training of Roman soldiers, designed to build 
        <strong>full-body power, grit, and mental discipline.</strong>.</p>
        <h5><i>Rucking&rarr;Functional strength&rarr;Isotonic movement&rarr;Loaded carries&rarr;Endurance conditioning</i></h5>
    </div>
    <div class="card">
        <h3>🛡️ Your duty and necessary equipment, if you wish:
 <i><small>Munus tuum, armaque necessaria, Si accipere volueris:</small></i> </h3>
        <p><small>
            - <b>Ruck Sack</b> (any backpack) (Choose one and use it for the entire length of the program) <br>
            - <b>Punching Bag</b> <small><i>preffered</i></small>, can use functional training if necessary (shadow boxing) <br>
            - <b>Bonus material</b> <small><i>not necessary, use if you have acesss</i></small> - Rope climb (Or ladder climb)
            <p><small><i>What will it be? </i></small></p>
        </small></p>
        <button><b>Enter The Hall</b> <i><small>Ingredere aulam:</small></i></button>
    </div>
    </section>
</template>

<style scoped>
    #welcome,
    .challenge,
    .benefits {
        display: flex;
        flex-direction: column;

    }

    #welcome {
        gap: 2.5rem;
    }
.benefits {
    gap: 1rem;
}
.challenge{
    gap: 2.1rem;
}

@media (min-width: 560px) {
    #welcome {
        gap: 2rem;
        padding: 2.1rem 0;
    }

    .benefits {
        gap: 0.5rem;
    }
}

</style>
