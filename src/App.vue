<template>
  <div class="box">
    <div class="box2">
      <h2>{{ titulo }}</h2>
      <div class="input-group">
        <input type="text" v-model="novaTarefa" v-on:keydown.enter="adicionarTarefa"/> <input type="date" v-model="data" v-on:keydown.enter="adicionarTarefa"/> <span class="input-group-btn">
          <button @click="adicionarTarefa" class="btn btn-primary">
            Adicionar tarefa
          </button>
        </span>
      </div>
      <ul>
        <li
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :class="{ removed: tarefa.checked }"
        >
          <input type="checkbox" v-model="tarefa.checked" />
          <label>{{ tarefa.titulo }}</label>
        </li>
      </ul>
    </div>
    <footer>
      <em>Altere aqui o título da sua lista  </em>
      <input v-model="titulo" type="text" />
    </footer>
  </div>

</template>

<script>
export default {
  name: "App",
  data() {
    return {
      titulo: "Minha lista de tarefas",
      novaTarefa: "",
      tarefas: [],
    };
  },
  methods: {
    adicionarTarefa() {
      this.tarefas.push({
        titulo: this.novaTarefa + " - " + this.data,
        checked: false,
      });
      this.novaTarefa = "";
    },
  },
};
</script>

<style>
.box {
  //background-color: #DAA520;
  //border: solid 3px black;
  color: black;
  font-family: Helvetica;
  font-size: 18px;
  text-align: center;
  line-height: 1.5;
  width: 500px;
  position: relative;
  margin-left: auto;
  margin-right: auto;
  top: 45%;
  margin: 20px auto 0px auto;
}
.box2 {
  background-color: #DAA520;
  border: solid 3px black;
}
ul li {
  list-style: none;
  font-size: 20px;
  line-height: 2.5;
}
.removed {
  color: gray;
}
.removed label {
  text-decoration: line-through;
}
footer {
  line-height: 3;
}
</style>