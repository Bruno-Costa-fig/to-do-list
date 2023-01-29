<template>
  <div ref="item" class="item" :class="item.finalizado ? 'box-shadow' : ''">
    <span :style="item.finalizado ? 'text-decoration: line-through; color: var(--preto);' : ''">{{ item.titulo }}</span>
    <div>

      <box-icon 
      class="icon" 
      :color="!item.finalizado ? 'white' : 'var(--preto)'" 
      name="check" 
      size="sm" 
      @click="$emit('finalizar')"
      />
      <box-icon 
      class="icon" 
      color="white" 
      name="trash" 
      size="sm" 
      @click="deletar"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "todo-item",
  props: {
    item: {
      type: Object,
      default: {
        titulo: "",
        finalizado: false
      }
    }
  },
  methods: {
    deletar(){
      this.$refs.item.classList.add('excluindo')

      setInterval(() => {
        this.$emit("deletar")
      }, 400);
    }
  }
}
</script>
<style scoped>
  .item {
    margin-top: 15px;
    padding: 10px;
    display: flex;
    justify-content: space-between;
    width: 480px;
    background: var(--todo);
    border-radius: 10px;
    transition: .2s ease-in-out;
    /* box-shadow: rgba(190, 190, 190, 0.132) 0px 7px 29px 0px; */
    /* box-shadow: rgba(16, 16, 16, 0.41) 0px 30px 60px -12px inset, rgba(0, 0, 0, 0.781) 0px 18px 36px -18px inset; */
  }
  
  .box-shadow {
    box-shadow: rgba(16, 16, 16, 0.687) 0px 2px 4px 0px inset;
  }

  .excluindo {
    animation: excluindo .5s;
  }

  @keyframes excluindo {
    0% {
      opacity: 0.8;
    } 100% {
      transform: translateX(-1000px);
      opacity: 0;
    }
  }
</style>