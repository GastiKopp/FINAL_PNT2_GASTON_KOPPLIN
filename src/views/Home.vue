<template>
  <div class="d-flex flex-column min-vh-100">
    <div class="container flex-grow-1 d-flex justify-content-start align-items-center pt-5 flex-column">

      <div class="card shadow p-4 w-100" style="max-width: 500px;">
        <h2 class="text-center mb-4">💰 Conversor de Pesos a Dólar Oficial</h2>
        <Conversor />
        <hr />
        <p class="text-muted mt-4 mb-0">
          <h4>
          <strong><u>Respuestas:</u></strong> 1:<strong>b</strong> 2:<strong>b,c</strong> 3:<strong>c</strong> 4:<strong>b,e</strong> 5:<strong>a,c</strong>
          </h4>
        </p>
      </div>
    </div>

<footer class="bg-secondary text-white text-center py-3 mt-auto">
  <p class="mb-0">Gastón Kopplin Alva - Final PNT2 - Julio 2025</p>
</footer>

  </div>
</template>

<script>
import Conversor from '@/components/Conversor.vue';

export default {
  components: {
    Conversor,
  },
};
</script>
