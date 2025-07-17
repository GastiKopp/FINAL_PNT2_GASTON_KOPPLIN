<template>
  <div>
    <div class="mb-3">
      <label for="monto" class="form-label">Ingrese monto en pesos $</label>
      <input
        type="number"
        id="monto"
        class="form-control"
        v-model.number="pesos"
        min="0"
      />
    </div>

    <div v-if="cotizacion">
      <p>
        Valor del dólar oficial venta
        <strong>${{ cotizacion }}</strong> - fecha:
        {{ fecha }}
      </p>
      <p>
        Valor convertido <strong>USD {{ valorConvertido }}</strong>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      pesos: 0,
      cotizacion: null,
      fecha: null,
      intervalo: null,
    };
  },
  computed: {
    valorConvertido() {
      if (!this.cotizacion) return "0.00";
      return (this.pesos / this.cotizacion).toFixed(2);
    },
  },
  methods: {
    async obtenerCotizacion() {
      try {
        const res = await axios.get("https://api.bluelytics.com.ar/v2/latest");
        this.cotizacion = res.data.oficial.value_sell;
        const ahora = new Date();
        this.fecha = ahora.toLocaleString();
      } catch (error) {
        console.error("Error al obtener cotización:", error);
      }
    },
  },
  mounted() {
    this.obtenerCotizacion();
    this.intervalo = setInterval(this.obtenerCotizacion, 2000);
  },
  beforeUnmount() {
    clearInterval(this.intervalo);
  },
};
</script>
