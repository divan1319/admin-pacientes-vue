<script setup>
import { reactive, ref } from "vue";
import Formulario from "./components/Formulario.vue";
import Header from "./components/Header.vue";
import Paciente from "./components/Paciente.vue";
import { uid } from "uid";
const pacientes = ref([]);
const paciente = reactive({
  id: null,
  nombre: "",
  propietario: "",
  email: "",
  alta: "",
  sintomas: "",
});

const guardarPaciente = () => {
  pacientes.value.push({
    ...paciente,
    id: uid(),
  });

  Object.assign(paciente, {
    nombre: "",
    propietario: "",
    email: "",
    alta: "",
    sintomas: "",
  });
};

const editarPaciente = (id) => {
  const pacienteEditar = pacientes.value.filter(p => p.id === id)[0]
  Object.assign(paciente,pacienteEditar)
};
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
        @guardar-paciente="guardarPaciente" />
      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h2 class="font-black text-3xl text-center">
          Ingreso de pacientes
        </h2>
        <p class="text-lg mt-5 text-center mb-10">
          Mascotas ingresadas
          <span class="text-indigo-600 font-bold">Administrar</span>
        </p>
        <div v-if="pacientes.length > 0">
          <Paciente
            v-for="paciente in pacientes"
            :paciente="paciente"
            @actualizar-paciente="editarPaciente" />
        </div>
        <p v-else class="mt-10 text-base font-bold text-center">
          No hay pacientes
        </p>
      </div>
    </div>
  </div>
</template>
