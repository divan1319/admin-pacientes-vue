<script setup>
import { reactive, ref } from "vue";
import Formulario from "./components/Formulario.vue";
import Header from "./components/Header.vue";
import Paciente from "./components/Paciente.vue";
const pacientes = ref([]);
const paciente = reactive({
  nombre: "",
  propietario: "",
  email: "",
  alta: "",
  sintomas: "",
});

const guardarPaciente = () => {
  pacientes.value.push({
    ...paciente,
  });

  Object.assign(paciente, {
    nombre: "",
    propietario: "",
    email: "",
    alta: "",
    sintomas: "",
  });
};

const editarPaciente = ()=>{
  
}
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />
    <div class="mt-12 md:flex">
      <Formulario
        v-model:nombre="paciente.nombre"
        v-model:propietario="paciente.propietario"
        v-model:email="paciente.email"
        v-model:alta="paciente.alta"
        v-model:sintomas="paciente.sintomas"
        @guardar-paciente="guardarPaciente"
      />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Pacientes en cola</h3>
        <div v-if="pacientes.length > 0">
          <Paciente v-for="paciente in pacientes" :paciente="paciente" />
        </div>
        <p v-else class="mt-10 text-base font-bold text-center">
          No hay pacientes
        </p>
      </div>
    </div>
  </div>
</template>
