<script setup>
const props = defineProps([
    'numero1',
    'numero2',
    'operacao',
    'editaNumero1',
    'editaNumero2',
    'trocarOperacao'
])
</script>

<template>
    <form @submit.prevent>
        <div class="row">
            <div class="col">
                <input type="number" class="form-control" placeholder="Digite o primeiro número" :value="props.numero1"
                    @input="props.editaNumero1" />
            </div>
            <div class="col">
                <input type="number" class="form-control" placeholder="Digite o segundo número" :value="props.numero2"
                    @input="props.editaNumero2" />
            </div>
            <div class="col-md-3">
                <select class="form-control" @change="props.trocarOperacao" :value="props.operacao">
                    <option value="soma">Soma (+)</option>
                    <option value="subtracao">Subtração (-)</option>
                    <option value="multiplicacao">Multiplicação (×)</option>
                    <option value="divisao">Divisão (÷)</option>
                </select>
            </div>
        </div>
    </form>
</template>

<!-- <script setup>
        const props = defineProps(['cadastrarTarefa', 'tarefaTemp', 'trocarFiltro', 'editaTarefaTemp']);
</script>
<template>
    <form @submit.prevent="props.cadastrarTarefa">
            <div class="row">
                <div class="col">
                    <input :value="props.tarefaTemp" @change="props.editaTarefaTemp" required type="text" placeholder="digite aqui os valores" class="form-control" />
                </div>
                <div class="col-md-2">
                    <button type="submit" class="btn btn-primary">Cadastrar</button>
                </div>
                <div class="col-md-2">
                    <select @change="props.trocarFiltro" class="form-control">
                        <option value="todas">Todas tarefas</option>
                        <option value="pendentes">Pendentes</option>
                        <option value="finalizadas">Finalizadas</option>
                    </select>
                </div>
            </div>
        </form>
</template> -->