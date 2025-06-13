<script setup>
import { reactive } from 'vue'
import Cabecalho from './components/Cabecalho.vue'
import Formulario from './components/Formulario.vue'

const estado = reactive({
  numero1: '',
  numero2: '',
  operacao: 'soma'
})

const calcular = () => {
  const n1 = Number(estado.numero1)
  const n2 = Number(estado.numero2)

  if (estado.numero1 === '' || estado.numero2 === '') {
    return ''
  }

  if (estado.operacao === 'soma') {
    return n1 + n2
  }

  if (estado.operacao === 'subtracao') {
    return n1 - n2
  }

  if (estado.operacao === 'multiplicacao') {
    return n1 * n2
  }

  if (estado.operacao === 'divisao') {
    if (n2 === 0) {
      return 'Erro: divisão por zero'
    } else {
      return n1 / n2
    }
  }

  return ''
}
</script>

<template>
  <div class="container">
    <Cabecalho />
    <Formulario
      :numero1="estado.numero1"
      :numero2="estado.numero2"
      :operacao="estado.operacao"
      :edita-numero1="evento => estado.numero1 = evento.target.value"
      :edita-numero2="evento => estado.numero2 = evento.target.value"
      :trocar-operacao="evento => estado.operacao = evento.target.value"
    />
    <h2 class="mt-4">Resultado: {{ calcular() }}</h2>
  </div>
</template>

<!-- <script setup>
  import { reactive } from 'vue'
  import Cabecalho from './components/Cabecalho.vue'
  import Formulario from './components/Formulario.vue'
  import ListaDeTarefas from './components/ListaDeTarefas.vue'

const estado = reactive({
  filtro: 'todas',
  tarefaTemp: '',
    tarefas: [
        {
            titulo: 'Estudar ES6',
            finalizada: false,
        },
        {
            titulo: 'Estudar SASS',
            finalizada: false,
        },
        {
            titulo: 'Ir para a academia',
            finalizada: true,
        }
    ]
})

  const getTarefasPendentes = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
}

const getTarefasFinalizadas = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
}

const getTarefasFiltradas = () => {
    const { filtro } = estado;

    switch (filtro) {
        case 'pendentes':
            return getTarefasPendentes();
        case 'finalizadas':
            return getTarefasFinalizadas();
        default:
            return estado.tarefas;
    }
}

const cadastraTarefa = () => {
    const tarefaNova = {
        titulo: estado.tarefaTemp,
        finalizada: false,
    }
    estado.tarefas.push(tarefaNova);
    estado.tarefaTemp = '';
}
</script>

<template>
  <div class="container">
    <Cabecalho :tarefas-pendentes="getTarefasPendentes().length" />
    <Formulario :trocar-filtro="evento => estado.filtro = evento.target.value" :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" />
    <ListaDeTarefas :tarefas="getTarefasFiltradas()" />
  </div>
</template>

-->
