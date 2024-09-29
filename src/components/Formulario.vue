<script setup>
import {ref, reactive} from 'vue'
import Alerta from "./Alerta.vue";

const alerta = reactive({
  type: '',
  color: '',
  message: '',
})

const paciente = reactive({
  nombreMascota: '',
  propietario: '',
  email: '',
  alta: '',
  sintomas: '',
})

const validate = () => {
  if (Object.values(paciente).includes('')) {
    alerta.type = 'error'
    alerta.color = 'text-red-500'
    alerta.message = 'Complete todos los campos'
  } else {
    alerta.type = 'success'
    alerta.color = 'text-green-500'
    alerta.message = 'Registrado exitosamente'
  }
}
</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Seguimiento Pacientes</h2>
    <p class="text-lg mt-5 text-center mb-10">
      Añade Pacientes y
      <span class="text-indigo-600 font-bold">Administralos</span>
    </p>
    <form
        @submit.prevent="validate"
        class="shadow-md bg-white rounded-lg py-10 px-5 mb-10 space-y-5"
    >
      <Alerta
          v-if="alerta.message"
          :alerta="alerta"
      />
      <div class="space-y-1">
        <label
            for="mascota"
            class="block text-gray-700 uppercase font-bold"
        >
          Nombre Mascota
        </label>
        <input
            v-model="paciente.nombreMascota"
            type="text"
            id="mascota"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            placeholder="Nombre"
        />
      </div>
      <div class="space-y-1">
        <label
            for="propietario"
            class="block text-gray-700 uppercase font-bold"
        >
          Nombre Propietario
        </label>
        <input
            v-model="paciente.propietario"
            type="text"
            id="propietario"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            placeholder="Nombre Propietario"
        />
      </div>
      <div class="space-y-1">
        <label
            for="email"
            class="block text-gray-700 uppercase font-bold"
        >
          Email
        </label>
        <input
            v-model="paciente.email"
            type="email"
            id="email"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            placeholder="Email del propietario"
        />
      </div>
      <div class="space-y-1">
        <label
            for="alta"
            class="block text-gray-700 uppercase font-bold"
        >
          Alta
        </label>
        <input
            v-model="paciente.alta"
            type="date"
            id="alta"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
        />
      </div>
      <div class="space-y-1">
        <label
            for="sintomas"
            class="block text-gray-700 uppercase font-bold"
        >
          Sintomas
        </label>
        <textarea
            v-model="paciente.sintomas"
            id="sintomas"
            class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            placeholder="Descripción los sintomas"
        />
      </div>
      <input
          type="submit"
          value="Registrar"
          class="cursor-pointer w-full bg-indigo-600 hover:bg-indigo-500 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
      />
    </form>
  </div>
</template>