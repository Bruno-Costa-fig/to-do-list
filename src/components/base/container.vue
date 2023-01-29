<template>
  <div class="container-base">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'container'
}
</script>

<style scoped>
.container-base {
  display: flex;
  flex-direction: column;
  justify-content: start;
  align-items: center;
  height: 100vh;
  width: 100vw;
  background: var(--preto);
  color: var(--verde-claro);

}
</style>