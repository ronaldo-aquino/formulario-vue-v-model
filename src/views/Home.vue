<template>
  <form @submit.prevent="processarFormulario">
    <input
      type="text"
      class="form-control my-2"
      placeholder="Digite seu nome aqui..."
      v-model.trim="tarefa.nome"
    />

    <div class="form-check form-check-inline">
      <input
        type="checkbox"
        id="check-1"
        class="form-check-input"
        v-model="tarefa.categorias"
        value="javascript"
      />
      <label for="check-1" class="form-check-label">Javascript</label>
    </div>

    <div class="form-check form-check-inline">
      <input
        type="checkbox"
        id="check-2"
        class="form-check-input"
        v-model="tarefa.categorias"
        value="nodejs"
      />
      <label for="check-2" class="form-check-label">Node.js</label>
    </div>

    <div class="mt-2">
      <div class="form-check form-check-inline">
        <input
          type="radio"
          id="radio-1"
          class="form-check-input"
          value="urgente"
          v-model="tarefa.estado"
        />
        <label for="radio-1" class="form-check-label">Urgente</label>
      </div>

      <div class="form-check form-check-inline">
        <input
          type="radio"
          id="radio-2"
          class="form-check-input"
          value="normal"
          v-model="tarefa.estado"
        />
        <label for="radio-2" class="form-check-label">Normal</label>
      </div>
    </div>

    <div class="mt-2">
      <input
        type="number"
        v-model.number="tarefa.numero"
        class="form-control"
      />
    </div>

    <button
      class="btn btn-dark btn-block mt-2"
      type="submit"
      :disabled="bloquear"
    >
      Processar
    </button>
  </form>
  <hr />
  <p>{{ tarefa }}</p>
</template>

<script>
export default {
  name: "Home",
  components: {},

  data() {
    return {
      tarefa: {
        nome: "",
        categorias: [],
        estado: "",
        numero: 0,
      },
    };
  },

  methods: {
    processarFormulario() {
      if (this.tarefa.nome.trim() === "") {
        console.log("Campo vazio");
        return;
      }

      console.log(this.tarefa);
      this.tarefa = { nome: "", categorias: [], estado: "", numero: 0 };
    },
  },

  computed: {
    bloquear() {
      return this.tarefa.nome.trim() === "" ? true : false;
    },
  },
};
</script>
