<script setup>
//importar o ref()
import {ref} from "vue";

const tarefas = ref(["Organizar a área de trabalho",
"Revisar e-mails",
 "Planejar o dia seguinte", 
 "Praticar exercício físico", 
 "Ler por 30 minutos",
  "Tomar banho"])

//Nova tarefa- precisa ser definida como ref()
const novaTarefa = ref("");

//função para remover cada item:
function removerTarefa(index) {
  tarefas.value.splice(index, 1)
  // remove 1 item pela posição clicada
}

//função para adicionar:
function adicionarTarefa(){
if(novaTarefa.value.trim()!== ""){
tarefas.value.push(novaTarefa.value.trim())
novaTarefa.value = ""
  }
}
</script>

<template>
  <h1> 📝Lista de Tarefas</h1>
    <div v-if="tarefas.length === 0">
    <p>🎉Parabéns! Você completou todas as tarefas!!!</p>
  </div>
  <ul v-else>
    <!-- v-for uma diretiva que serve para fazer  loops-->
    <li v-for="(tarefa, index) in tarefas" :key="index">{{ tarefa }} 
      <button @click="removerTarefa(index)">❌Remover</button>
    </li>
  </ul>
  <section>
    <input
    type="text"
    placeholder="Digite uma nova tarefa"
    v-model="novaTarefa">
    <!--a diretiva v-model sincroniza um valor de uma variavel ao input-->
    <button @click="adicionarTarefa">Adicionar tarefa</button>
  </section>
</template>

<style lang="scss">
body {
  background-color: #42a7ff;
  margin: 0;
  font-family: Arial, sans-serif;
}

h1 {
  text-align: center;
  margin: 50px 0 20px;
  font-size: 3rem;
  color: black;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0 auto;
  max-width: 400px;

  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 10px 0;
    padding: 10px;
    border: 1px solid black;
    border-radius: 10px;
    background-color: rgb(247, 247, 185);

    button {
      background-color: white;
      color: black;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      padding: 5px 10px;
      font-size: 15px;

      &:hover {
        background-color: blue;
      }
    }
  }
}


input[type="text"] {
  padding: 20px;
  font-size: 14px;
  border: 1px solid blue;
  border-radius: 5px;
  width: 400px;
}

section {
  display: flex;
  justify-content: center;
  gap: 20px;
  margin-top: 20px;
}
</style>