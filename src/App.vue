<script setup>
import { reactive, ref } from "vue";
import Formulario from "./components/Formulario.vue";
import Header from "./components/Header.vue";

const pacientes = ref([]);
const paciente = reactive({
  nombre: "",
  propietario: "",
  email: "",
  alta: "",
  sintomas: "",
});
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />
    <div class="mt-12 md:flex">
      <Formulario 
      v-model:nombre="paciente.nombre"
      v-model:propietario="paciente.nombre"
      v-model:email="paciente.nombre"
      v-model:alta="paciente.nombre"
      v-model:sintomas="paciente.nombre"
      />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Pacientes en cola</h3>
        <div v-if="pacientes.length > 0"></div>
        <p v-else class="mt-10 text-base font-bold text-center">
          No hay pacientes
        </p>
      </div>
    </div>
  </div>
</template>
