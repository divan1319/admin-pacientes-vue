<script setup>
import { reactive, ref } from 'vue';
import Alerta from "./Alerta.vue";

    const alerta = reactive({
        tipo:'',
        mensaje:''
    })


    const validar = ()=>{
        if (Object.values(paciente).includes('')) {
            alerta.mensaje='Todos los campos son obligatorios'
            alerta.tipo = 'error'
            return
        }
    }

    defineEmits(['update:nombre',])
</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Seguimiento de Pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Agregar pacientes
      <span class="text-indigo-600 font-bold">Administrar</span>
    </p>
    <Alerta
    v-if="alerta.mensaje"
    :alerta="alerta"
    />
    <form @submit.prevent="validar" class="bg-white shadow-md rounded-lg py-10 px-5 mb-10">
        {{ paciente.nombre }}
      <div class="mb-5">
        <label for="mascota" class="block text-gray-700 uppercase font-bold"
          >Nombre Mascota</label
        >
        <input
          type="text"
          id="mascota"
          class="border-2 w-full mt-2 p-2 placeholder-gray-400 rounded-md"
          @input="$emit('update:nombre', $event.target.value)"
          
        />
      </div>
      <div class="mb-5">
        <label for="propietario" class="block text-gray-700 uppercase font-bold"
          >Nombre Propietario</label
        >
        <input
          type="text"
          id="propietario"
          class="border-2 w-full mt-2 p-2 placeholder-gray-400 rounded-md"
          v-model="paciente.propietario"
        />
      </div>
      <div class="mb-5">
        <label for="email" class="block text-gray-700 uppercase font-bold">
          Email</label
        >
        <input
          type="email"
          id="email"
          class="border-2 w-full mt-2 p-2 placeholder-gray-400 rounded-md"
          v-model="paciente.email"
        />
      </div>
      <div class="mb-5">
        <label for="alta" class="block text-gray-700 uppercase font-bold"
          >Alta</label
        >
        <input
          type="date"
          id="alta"
          class="border-2 w-full mt-2 p-2 placeholder-gray-400 rounded-md"
          v-model="paciente.alta"
        />
      </div>
      <div class="mb-5">
        <label for="sintomas" class="block text-gray-700 uppercase font-bold"
          >Sintomas</label
        >
        <textarea
          type="text"
          id="sintomas"
          class="border-2 w-full mt-2 p-2 placeholder-gray-400 rounded-md h-40"
          v-model="paciente.sintomas"
        />
      </div>
      <input
        type="submit"
        class="bg-indigo-600 w-full p-3 text-white uppercase hover:bg-indigo-700 cursor-pointer transition-colors"
        value="Registrar Paciente"
      />
    </form>
  </div>
</template>
