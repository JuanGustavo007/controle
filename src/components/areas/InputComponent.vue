<template>
  <div>
    <div class="container mt-5">
      <div class="row gap-3">
        <div class="col">
          <form action="">
            <label for="exampleInputEmail1" class="form-label">Descrição</label>
            <input
              type="text"
              class="form-control descr"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
              v-model="descricao"
            />
          </form>
        </div>
        <div class="col">
          <form action="">
            <label for="exampleInputEmail1" class="form-label">Valor</label>
            <input
              type="number"
              class="form-control valor"
              id="exampleInputEmail1"
              aria-describedby="emailHelp"
              v-model="valor"
            />
          </form>
        </div>
        <div class="col align-items-center checks d-flex gap-3">
          <div class="form-check">
            <input
              class="form-check-input check-entrada"
              type="radio"
              name="flexRadioDefault"
              id="flexRadioDefault1"
              value="entrada"
              v-model="tipo"
            />
            <label class="form-check-label" for="flexRadioDefault1">
              Entrada
            </label>
          </div>
          <div class="form-check">
            <input
              class="form-check-input check-saida"
              type="radio"
              name="flexRadioDefault"
              id="flexRadioDefault2"
              value="saida"
              v-model="tipo"
            />
            <label class="form-check-label" for="flexRadioDefault2">
              Saída
            </label>
          </div>
          <div class="col d-flex botao">
            <button class="btn btn-primary" @click="navegarPara()">
              Adicionar
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "InputComponent",
  data() {
    return {
      descricao: "",
      valor: 0,
      tipo: "",
    };
  },

  props: {
    funcaoCall: Function,
  },
  methods: {
    acao() {
      console.log("opa");
    },
    navegarPara() {
      this.$emit("funcaoCall", {
        valorDescricao: this.descricao,
        valorValor: this.valor,
        valorTipo: this.tipo,
      });
      this.descricao = "";
      this.valor = 0;
      this.tipo = "";
    },
  },
};
</script>

<style scoped>
.container {
  padding: 20px;
  border: 3px solid black;
  background-color: white;
}
.checks {
  justify-content: space-between;

  display: flex;
}

.botao {
  justify-content: flex-end;
}
</style>
