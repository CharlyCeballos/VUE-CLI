<template>
  <h2>Tipo de cuenta: {{ cuenta }}</h2>
  <h2>Saldo: {{ saldo }}</h2>
  <h2>Estado: {{ estado ? 'activa':'inactiva' }}</h2>
  <div v-for="(servicio, index) in servicios" :key="index">
    <lu>{{ index }} - {{ servicio }}</lu>
  </div>
  <AccionSaldo 
    texto="Aumentar "
    @accion="aumentar"
  />
  <AccionSaldo 
    texto="Disminuir "
    @accion="disminuir"
    :desactivar="desactivar"
  />
</template>

<script>
  import AccionSaldo from "./AccionSaldo.vue";

  export default {
    components: {
      AccionSaldo
    },

    data() {
      return {
        saldo: 1000,
        cuenta: 'visa',
        estado: true,
        servicios: [
          'giro',
          'abono',
          'transferencia',
        ],
        desactivar: false,
      }
    },

    methods: {
      aumentar() {
        this.saldo = this.saldo + 100
        this.desactivar = false
      },

      disminuir() {
        if (this.saldo === 0) {
          this.desactivar = true
          alert("Saldo agotado!")
          return
        }
        this.saldo = this.saldo - 100
      },

    },

  }
</script>

<style>

</style>