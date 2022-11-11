<template>
  <div>
    <HeaderComponent />
    <div class="container mt-5">
      <div class="row gap-3">
        <div class="col">
          <TotaisComponent class="entrada">
            <div class="d-flex flex-column arrumar">
              <h1>Entradas <i class="bi bi-arrow-up"></i></h1>
              <p class="valores-cards">{{ entrada }}</p>
            </div>
          </TotaisComponent>
        </div>
        <div class="col">
          <TotaisComponent class="saida">
            <div class="d-flex flex-column arrumar">
              <h1>Saídas <i class="bi bi-arrow-down"></i></h1>
              <p class="valores-cards">{{ saida }}</p>
            </div>
          </TotaisComponent>
        </div>
        <div class="col">
          <TotaisComponent :style="{ backgroundColor: cor }" class="total">
            <div @mouseenter="tool" class="d-flex flex-column arrumar">
              <h1>Total</h1>
              <p class="valores-cards">{{ (total = entrada - saida) }}</p>
            </div>
          </TotaisComponent>
        </div>
      </div>
    </div>
    <InputComponent @funcaoCall="callFilho($event)"></InputComponent>
    <ListaComponent></ListaComponent>
  </div>
</template>

<script>
import HeaderComponent from "./components/areas/HeaderComponent.vue";
import TotaisComponent from "./components/areas/TotaisComponent.vue";
import InputComponent from "./components/areas/InputComponent.vue";
import ListaComponent from "./components/areas/ListaComponent.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    TotaisComponent,
    InputComponent,
    ListaComponent,
  },
  data() {
    return {
      descricao: "",
      valor: 0,
      tipo: "",
      entrada: 0,
      saida: 0,
      total: 0,
      cor: "",
    };
  },
  methods: {
    callFilho(p) {
      // this.descricao = valorDescricao;
      // this.valor = ValorSaida;
      // this.tipo = ValorTipo;

      //
      ///
      ///
      //
      //
      //

      ///

      // const inputEntrada = document.querySelector(".descr");
      // inputEntrada.value = "";
      // const inputValor = document.querySelector(".valor");
      // inputValor.value = 0;
      // const inputCheckEntrada = document.querySelector(".check-entrada");
      // const inputCheckSaida = document.querySelector(".check-saida");
      // inputCheckEntrada.value = "";
      // inputCheckSaida.value = "";
      // valorDescricao = "";
      // ValorSaida = 0;
      // ValorTipo = "";
      // console.log(inputEntrada);

      this.descricao = p.valorDescricao;
      this.valor = p.valorValor;
      this.tipo = p.valorTipo;
      if (p.valorTipo === "entrada") {
        this.entrada += p.valorValor;
        p.valorValor = 0;
        p.ValorTipo = "";
        p.valorValor = "";
        if (this.valor > 0) {
          const selecionarLista = document.querySelector("ul");
          const adicionarLi = document.createElement("li");
          adicionarLi.innerText = `Atividade: ${this.descricao} com o valor de R$ ${this.valor} e é uma ${this.tipo}.`;
          selecionarLista.appendChild(adicionarLi);
          console.log(selecionarLista, adicionarLi);
        }
      } else if (p.valorTipo === "saida") {
        this.saida += p.valorValor;
        p.valorValor = 0;
        p.ValorTipo = "";
        p.valorValor = "";
        if (this.valor > 0) {
          const selecionarLista = document.querySelector("ul");
          const adicionarLi = document.createElement("li");
          adicionarLi.innerText = `Atividade: ${this.descricao} com o valor de R$ ${this.valor} e é uma ${this.tipo}.`;
          selecionarLista.appendChild(adicionarLi);
          console.log(selecionarLista, adicionarLi);
        }
      } else {
        alert(
          "Por favor Preencha o campo com o tipo, se é uma entrada ou saída."
        );
      }
      console.log(p.valorValor);
      console.log(p);
    },
    tool() {
      const selecionarTotal = document.querySelector(".total");
      console.log(selecionarTotal);

      selecionarTotal.setAttribute("data-bs-toggle", "tooltip");
      selecionarTotal.setAttribute("data-bs-placement", "top");
      selecionarTotal.setAttribute(
        "title",
        "Aqui fica o valor total de seu controle financeiro"
      );
      console.log(selecionarTotal);

      // data-bs-toggle="tooltip" data-bs-placement="top" title="Tooltip on top"
    },
  },
  watch: {
    total(novoValor, valorAntigo) {
      console.log(novoValor, valorAntigo);
      if (novoValor > 0) {
        this.cor = "green";
      } else if (novoValor === 0) {
        this.cor = "white";
      } else {
        this.cor = "red";
      }
    },
  },
};
</script>

<style>
.col {
  padding: 0;
}
.entrada {
  background-color: rgba(173, 255, 47, 0.4);
}
.saida {
  background-color: rgb(255, 0, 0, 0.4);
  height: 100%;
}
.valores-cards {
  font-size: 2rem;
}
p,
h1 {
  font-family: monospace;
}

#app {
  background-color: blanchedalmond;
}
body {
  background-color: blanchedalmond;
}
.total {
  background-color: white;
  height: 100%;
}
li {
  background-color: rgb(253, 253, 253);
  padding: 10px;
  list-style: none;
  border: 2px solid black;
  margin-bottom: 5px;
}
ul {
  padding: 0;
}
.arrumar {
  display: flex;
  justify-content: center;
  height: 100%;
}
.arrumar p {
  margin-bottom: 0;
}
.arrumar h1 {
  margin-bottom: 0;
}
</style>
