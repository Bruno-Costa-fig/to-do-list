<template>
  <button class="botaoAdicionar">{{ text }}</button>
</template>

<script>
export default {
  name: 'botao-adicionar',
  props: {
    text: {
      type: String,
      default: ""
    }
  }
}
</script>

<style scoped>
  .botaoAdicionar {
    padding: 10px 10px;
    background: var(--verde-claro);
    color: var(--branco);
    border: none;
    border-radius: 0 10px 10px 0;
  }
</style>