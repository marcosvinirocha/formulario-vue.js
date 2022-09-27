<template>
  <div class="container">
    <div class="row">
      <div class="col-6 bg-light">
        <span class="fs-4">ENTRADA DE DADOS</span>
        <hr />
        <form @reset.prevent="resetar($event)">
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Nome:</label>
            <div class="col">
              <input type="text" class="form-control" v-model.lazy="form.nome" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">E-mail:</label>
            <div class="col">
              <input type="email" class="form-control" v-model="form.email" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Senha:</label>
            <div class="col">
              <input type="password" class="form-control" v-model.trim="form.senha" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Idade:</label>
            <div class="col">
              <input type="number" class="form-control" v-model.number="form.idade" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Gênero:</label>
            <div class="col">
              <div class="form-check form-check-inline">
                <input class="form-check-input" type="radio" value="Feminino" v-model="form.genero" />
                <label class="form-check-label"> Feminino </label>
              </div>
              <div class="form-check form-check-inline">
                <input class="form-check-input" type="radio" value="Masculino" v-model="form.genero" />
                <label class="form-check-label"> Masculino </label>
              </div>
            </div>
          </div>

          <div class="mb-3 row">
            <label class="col-3 col-form-label">Licença:</label>
            <div class="col">
              <div class="form-check form-switch">
                <input class="form-check-input" type="checkbox" v-model="form.licenca" true-value="SIM"
                  false-value="NÃO" />
                <label class="form-check-label">Li e aceito os termos</label>
              </div>
            </div>
          </div>

          <div class="mb-3 row">
            <label class="col-3 col-form-label">Interesses:</label>
            <div class="col">
              <div class="form-check">
                <input class="form-check-input" type="checkbox" value="JavaScript" v-model="form.interesses" />
                <label class="form-check-label"> JavaScript </label>
              </div>
              <div class="form-check">
                <input class="form-check-input" type="checkbox" value="VueJS" v-model="form.interesses" />
                <label class="form-check-label"> VueJS </label>
              </div>
              <div class="form-check">
                <input class="form-check-input" type="checkbox" value="Angular" v-model="form.interesses" />
                <label class="form-check-label"> Angular </label>
              </div>
              <div class="form-check">
                <input class="form-check-input" type="checkbox" value="NodeJS" v-model="form.interesses" />
                <label class="form-check-label"> NodeJS </label>
              </div>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Telefone:</label>
            <div class="col">
              <input type="text" class="form-control" v-model="form.telefone" v-maska="'(##) #####-####'" />
              <small class="text-muted">Formato: 11 97777-5555</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">CEP:</label>
            <div class="col">
              <input type="text" class="form-control" v-model="form.cep" v-maska="'#####-###'" />
              <small class="text-muted">Formato: 00000-000</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">CPF:</label>
            <div class="col">
              <input type="text" class="form-control" v-model="form.cpf" v-maska="'###.###.###-##'" />
              <small class="text-muted">Formato: 000.000.000-00</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">CNPJ:</label>
            <div class="col">
              <input type="text" class="form-control" v-model="form.cnpj" v-maska="'##.###.###/####-##'" />
              <small class="text-muted">Formato: 00.000.000/0000-00</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Cartão de Crédito:</label>
            <div class="col">
              <input type="text" class="form-control" v-model="form.cartaoDeCredito" v-maska="'#### #### #### ####'" />
              <small class="text-muted">Formato: 0000 0000 0000 0000</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Placa Veículo:</label>
            <div class="col">
              <input type="text" class="form-control" v-model="form.placaVeiculo" v-maska="'AAA-####'" />
              <small class="text-muted">Formato: AAA-0000</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Placa Veículo Mercosul:</label>
            <div class="col">
              <input type="text" class="form-control" v-model="form.placaVeiculoMercosul" v-maska="'AAA#A##'" />
              <small class="text-muted">Formato: AAA0A00</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">RG:</label>
            <div class="col">
              <input type="text" class="form-control" v-model="form.rg" v-maska="'#*-X'" />
              <small class="text-muted">Formato: Sem padrão</small>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Data:</label>
            <div class="col">
              <input type="date" class="form-control" v-model="form.data" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Data/hora local:</label>
            <div class="col">
              <input type="datetime-local" class="form-control" v-model="form.dataHoraLocal" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Mês:</label>
            <div class="col">
              <input type="month" class="form-control" v-model="form.mes" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Semana:</label>
            <div class="col">
              <input type="week" class="form-control" v-model="form.semana" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Hora:</label>
            <div class="col">
              <input type="time" class="form-control" v-model="form.hora" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Cor:</label>
            <div class="col">
              <input type="color" class="form-color" v-model="form.color" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Valor limite:</label>
            <div class="col">
              <input type="range" class="form-range" min="0" max="100" step="1" v-model="form.alcance" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Escondido:</label>
            <div class="col">
              <input type="hidden" class="form-control" v-model="form.escondido" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Upload:</label>
            <div class="col">
              <input type="file" class="form-control" multiple @change="selecionarArquivos($event)" />
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Descrição:</label>
            <div class="col">
              <textarea class="form-control" rows="3" v-model="form.descricao"></textarea>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Cursos:</label>
            <div class="col">
              <select class="form-select" v-model="form.curso">
                <option value="" disabled>--- Selecione uma opção</option>
                <option v-for="curso in cursos" :key="curso.id" :value="curso.id">
                  {{ curso.curso }}
                </option>
              </select>
            </div>
          </div>
          <div class="mb-3 row">
            <label class="col-3 col-form-label">Avaliação:</label>
            <div class="col">
              <!-- <input-estrelas :numero-estrelas="5" @avaliar="form.avaliacao = $event" /> -->
              <input-estrelas :numero-estrelas="5" v-model:avaliar="form.avaliacao " />

            </div>
          </div>
          <hr />
          <div class="mb-3 row">
            <div class="col d-flex justify-content-between">
              <button class="btn btn-secondary" type="reset">Limpar</button>
              <button class="btn btn-success" type="button" @click="enviar($event)">
                Enviar (btn)
              </button>
              <button class="btn btn-success" type="submit">
                Enviar (submit)
              </button>
            </div>
          </div>
        </form>
      </div>

      <div class="col-6 text-white bg-secondary" :style="'background-color:' + form.color + '!important'">
        <span class="fs-4">ESTADO DO OBJETO</span>
        <hr />
        <div class="mb-5 row">
          <span>{{ form }}</span>
        </div>

        <span class="fs-4">SAÍDA DE DADOS</span>
        <hr />
        <div class="mb-3 row">
          <span>Nome: {{ form.nome }}</span>
        </div>
        <div class="mb-3 row">
          <span>E-mail: {{ form.email }}</span>
        </div>
        <div class="mb-3 row">
          <span>Senha: {{ form.senha }}</span>
        </div>
        <div class="mb-3 row">
          <span>Idade: {{ form.idade }}</span>
        </div>
        <div class="mb-3 row">
          <span>Gênero: {{ form.genero }}</span>
        </div>
        <div class="mb-3 row">
          <span>Licença: {{ form.licenca }}</span>
        </div>
        <div class="mb-3 row">
          <span>Interesses:</span>
          <ul>
            <li v-for="(interesse, index) in form.interesses" :key="index">
              {{ interesse }}
            </li>
          </ul>
        </div>
        <div class="mb-3 row">
          <span>Telefone: {{ form.telefone }}</span>
        </div>
        <div class="mb-3 row">
          <span>CEP: {{ form.cep }}</span>
        </div>
        <div class="mb-3 row">
          <span>CPF: {{ form.cpf }}</span>
        </div>
        <div class="mb-3 row">
          <span>CNPJ: {{ form.cnpj }}</span>
        </div>
        <div class="mb-3 row">
          <span>Cartão de Crédito: {{ form.cartaoDeCredito }}</span>
        </div>
        <div class="mb-3 row">
          <span>placaVeiculo: {{ form.placaVeiculo }}</span>
        </div>
        <div class="mb-3 row">
          <span>placaVeiculoMercosul: {{ form.placaVeiculoMercosul }}</span>
        </div>
        <div class="mb-3 row">
          <span>rg: {{ form.rg }}</span>
        </div>
        <div class="mb-3 row">
          <span>Data: {{ form.data }}|{{
          $moment(form.data).format("DD/MM/YYYY")
          }}</span>
        </div>
        <div class="mb-3 row">
          <span>Data/hora local: {{ form.dataHoraLocal }} </span>
          <ul>
            <li>{{ $moment(form.dataHoraLocal).format("dddd") }}</li>
            <li>{{ $moment(form.dataHoraLocal).format("LLLL") }}</li>
          </ul>
        </div>
        <div class="mb-3 row">
          <span>Mês {{ form.mes }}:</span>
        </div>
        <div class="mb-3 row">
          <span>Semana:{{ form.semana }}</span>
        </div>
        <div class="mb-3 row">
          <span>Hora:{{ form.hora }}</span>
        </div>
        <div class="mb-3 row">
          <span>Cor: {{ form.color }} </span>
        </div>
        <div class="mb-3 row">
          <span>Valor limite: {{ form.alcance }} </span>
        </div>
        <div class="mb-3 row">
          <span>Escondido: {{ form.escondido }} </span>
        </div>
        <div class="mb-3 row">
          <span>Upload:</span>
          <ul>
            <li v-for="(arquivo, index) in form.arquivos" :key="index">
              {{ arquivo.name }}
            </li>
          </ul>
        </div>
        <div class="mb-3 row">
          <span>Descrição: </span>
          <!-- <pre>{{form.descricao}}</pre> -->
          <div style="white-space: pre">{{ form.descricao }}</div>
        </div>

        <div class="mb-3 row">
          <span>Curso: {{ form.curso }} </span>
        </div>
        <div class="mb-3 row">
          <span>Avaliação: {{ form.avaliacao }} </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import InputEstrelas from "./InputEstrelas.vue";
export default {
  components: {
    InputEstrelas,
  },
  name: "Formulario",
  data: () => ({
    cursos: [
      { id: 1, curso: "Banco de dados relacionais" },
      { id: 2, curso: "Desenvolvimento Web Avançado com Vue" },
      { id: 3, curso: "Desenvolvimento Web Avançado com Laravel" },
      { id: 4, curso: "Curso Completo do Desenvolvedor Nodejs e MongoDB" },
    ],
    form: {},
    formEstadoInicial: {
      nome: "Jorge",
      email: "jorge@teste.com.br",
      senha: "123456",
      idade: 25,
      licenca: "SIM",
      interesses: ["VueJS", "Angular"],
      genero: "Feminino",
      telefone: "",
      cep: "",
      cpf: "",
      cnpj: "",
      cartaoDeCredito: "",
      placaVeiculo: "",
      placaVeiculoMercosul: "",
      rg: "",
      data: "",
      dataHoraLocal: "",
      mes: "",
      semana: "",
      hora: "",
      color: "#6C757d",
      alcance: 5,
      escondido: "esse input esta escondido",
      arquivos: {},
      descricao: "",
      curso: "",
      avaliacao: 0
    },
  }),
  created() {
    this.resetar();
  },
  methods: {
    selecionarArquivos(event) {
      // console.log(event.target.files);
      this.form.arquivos = event.target.filess;
    },
    enviar(e) {
      console.log(e);
      console.log(this.form);

      const formEnvio = Object.assign({}, this.form);

      console.log(formEnvio);
    },
    resetar() {
      this.form = Object.assign({}, this.formEstadoInicial);
    },
  },
};
</script>
