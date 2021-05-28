<template>
  <Button @click="accion" :disabled="desactivar">{{ texto }} saldo</Button>
</template>

<script>
  export default {
    props: {
      texto: String,
      desactivar: {
        type: Boolean,
        default: false,
      },
    },

    methods: {
      accion() {
        this.$emit('accion')
      }
    },

  }
</script>

<style>

</style>