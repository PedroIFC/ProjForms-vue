<script setup>
import { ref, reactive } from "vue";

const user = ref({
    name: '',
    email: '',
    password: '',
    born: '',
    address: '',
    state: '',
    linguagens: [],
    bio: '',
})

const cidadeUser = ref([""])

const estados = ref([
    { 'name': 'Acre', 'sigla': 'AC' },
    { 'name': 'Alagoas', 'sigla': 'AL' },
    { 'name': 'Amapá', 'sigla': 'AP' },
    { 'name': 'Amazonas', 'sigla': 'AM' },
    { 'name': 'Bahia', 'sigla': 'BA' },
    { 'name': 'Ceará', 'sigla': 'CE' },
    { 'name': 'Distrito Federal', 'sigla': 'DF' },
    { 'name': 'Espírito Santo', 'sigla': 'ES' },
    { 'name': 'Goiás', 'sigla': 'GO' },
    { 'name': 'Maranhão', 'sigla': 'MA' },
    { 'name': 'Mato Grosso', 'sigla': 'MT' },
    { 'name': 'Mato Grosso do Sul', 'sigla': 'MS' },
    { 'name': 'Minas Gerais', 'sigla': 'MG' },
    { 'name': 'Pará', 'sigla': 'PA' },
    { 'name': 'Paraíba', 'sigla': 'PB' },
    { 'name': 'Paraná', 'sigla': 'PR' },
    { 'name': 'Pernambuco', 'sigla': 'PE' },
    { 'name': 'Piauí', 'sigla': 'PI' },
    { 'name': 'Rio de Janeiro', 'sigla': 'RJ' },
    { 'name': 'Rio Grande do Norte', 'sigla': 'RN' },
    { 'name': 'Rio Grande do Sul', 'sigla': 'RS' },
    { 'name': 'Rondônia', 'sigla': 'RO' },
    { 'name': 'Roraima', 'sigla': 'RR' },
    { 'name': 'Santa Catarina', 'sigla': 'SC' },
    { 'name': 'São Paulo', 'sigla': 'SP' },
    { 'name': 'Sergipe', 'sigla': 'SE' },
    { 'name': 'Tocantins', 'sigla': 'TO' },
    { 'name': 'Estrangeiro', 'sigla': 'EX' }
])

const hobbiesSelecionado = ref([])

const linguagens = ref([' C#', ' Python', ' C++', ' JavaScript', ' PHP', ' Swift', ' Java', ' Go', ' SQL', ' Ruby'])

const confirmPassword = ref("")

let mostrarInformacoes = ref(true)

function mostrarInfoBtn() {
    mostrarInformacoes.value = true
}

function ocultarInfoBtn() {
    mostrarInformacoes.value = false
}

</script>

<template>
    <main>
        <transition name="form" mode="out-in">
            <forms v-if="mostrarInformacoes == true"
                class="flex justify-center items-center w-screen h-screen bg-green-500">
                <div class="flex flex-col w-40/1 h-95/1 rounded-xl bg-white overflow-y-auto px-16">
                    <div class="flex sticky justify-center w-full font-poppins py-5">
                        <h1 class="text-6xl">Forms</h1>
                    </div>
                    <div class="flex flex-row w-full px-10">
                        <div class="w-45/1">
                            <input class="input-css w-full border-b-green-500 border-b-2 " v-model="user.name"
                                placeholder="Nome" type="text" required>
                        </div>
                        <div class="w-10/1"></div>
                        <div class="w-45/1">
                            <input class="input-css w-full" v-model="user.email" placeholder="Email" type="email" required>
                        </div>
                    </div>

                    <div class="flex flex-col w-full px-10 gap-5 mt-5">
                        <div class="sobre-input">
                            <input class="input-css" v-model="user.password" placeholder="Senha" type="password" required>
                        </div>

                        <div class="sobre-input">
                            <input class="input-css" v-model="user.confirmPassword" placeholder="Confirme sua senha"
                                type="password" required>
                        </div>

                        <div class="sobre-input">
                            <input class="input-css" v-model="user.born" placeholder="Data de Nascimento" type="text"
                                onfocus="this.type='date'" required>
                        </div>

                        <div class="sobre-input">
                            <input class="input-css" v-model="user.address" placeholder="Endereço" type="text" required>
                        </div>

                        <div class="sobre-input">
                            <input class="input-css" v-model="user.cidadeUser" placeholder="Cidade" type="text" required>
                        </div>

                        <div class="sobre-input">
                            <select v-model="estado" class="input-css select-css" name="" id="">
                                <option disabled selected value="none">Estado</option>
                                <option class="op-css" v-for="(value, index) in estados" :key="index" value="value.sigla">
                                    {{ value.name }} - {{ value.sigla }}
                                </option>
                            </select>
                        </div>
                        <div class="sobre-input">
                            <input class="input-css" v-model="user.hobbies" placeholder="Hobbies" type="text" required>
                        </div>
                        <div class="sobre-inputs-2">
                            <div class="">
                                <label for="">Linguagens de programação</label>
                            </div>
                            <div class="columns-5">
                                <label v-for="(value, index) of linguagens" :key="index" class="flex flex-col items-center">
                                    {{ value }}
                                    <input type="checkbox" v-model="user.linguagens" :value="value">
                                </label>
                            </div>
                        </div>
                    </div>
                    <div class="flex justify-center p-5">
                        <button @click="ocultarInfoBtn()" class="bg-green-500 text-white rounded-2xl w-28 p-2"
                            type="submit">
                            enviar
                        </button>
                    </div>
                </div>
            </forms>

            <!--Reultado Formulario-->

            <div v-else @submit.prevent="mostrarInfoBtn"
                class="flex justify-center items-center w-screen h-screen bg-green-500">
                <div class="flex flex-col w-40/1 h-95/1 rounded-xl bg-white overflow-y-auto px-16 bg-red-400">
                    <div class="flex sticky justify-center w-full font-poppins py-5">
                        <h1 class="text-6xl font-poppins">Forms</h1>
                    </div>
                    
                    </div>
                </div>
            </div>


        </transition>
    </main>
</template>

<style>
input:focus,
.select-css:focus {
    outline: none;
    color: #000
}

input,
.select-css,
.op-css {
    border-bottom: 2px solid rgb(70, 180, 70);
    background-color: transparent;
}

.select-css {
    position: relative;
}

.sobre-input {
    width: 100%;
}

.input-css {
    width: 100%;
    font-size: larger;
}

.input-css::placeholder {
    color: #000;
}
</style>