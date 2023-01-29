<template>
  <container>
    <h1 class="titulo">To do list</h1>
    <div class="container">
      <label>Digite sua tarefa: <input v-bind="$attrs" placeholder="Mensagem" type="text" v-model="todoItem.titulo" /></label>
      <botao-adicionar @click.prevent="adicionarItem" text="+ adicionar" />
    </div>
    <div v-for="item in todoList" :key="item.titulo">
      <todo-item @finalizar="item.finalizado = !item.finalizado" @deletar="deletarItem(item)" :item="item" />
    </div>
  </container>
</template>

<script>
import container from "./components/base/container.vue"
import botaoAdicionar from "./components/botaoAdicionar.vue";
import todoItem from "./components/todoItem.vue";

export default {
  components: {
    container,
    botaoAdicionar,
    todoItem
  },
  data() {
    return {
      todoItem: {
        titulo: "",
        finalizado: false
      },
      todoList: []
    }
  },
  methods: {
    adicionarItem(){
      let item = this.todoItem

      // Validação se o título não está vazio
      if(this.todoItem.titulo == ""){
        alert("O título não pode ficar vazio!")
        return
      }

      if(this.todoList.filter(x => x.titulo == item.titulo).length > 0){
        alert("Já existe uma mensagem com este texto!")
        this.todoItem.titulo = ""
        return
      }

      this.todoList.push({...item})
      this.todoItem = {
        titulo: "",
        finalizado: false
      }

    },
    deletarItem(item){
      this.todoList = this.todoList.filter(x => x.titulo != item.titulo)
    }
  }
}
</script>

<style scoped>
.titulo {
  margin: 20px 0;
}

.container {
  width: 100%;
  align-items: baseline;
}

input {
  width: 480px;
  padding: 10px 10px;
  border: none;
  border-radius: 10px 0 0 10px;
}
</style>