<script setup>
import { reactive } from 'vue';
import Alerta from './Alerta.vue'

const alerta = reactive({
  tipo: '',
  mensaje: '',
})

defineEmits(['update:nombre', 'update:propietario', 'update:email', 'update:alta', 'update:sintomas'])

const validar = () => {
  if(Object.values(paciente).includes('')){
    alerta.mensaje = 'Todos los campos son obligatorios'
    alerta.tipo = 'error'
    return
  }
  console.log('Agregando...');
}

</script>

<template>
  <div class="md:w-1/2">
    <h2 class="font-black text-3xl text-center">Seguimiento Paciente</h2>

    <p class="texy-lg mt-5 text-center mb-10">
      Añade Pacientes
      <span class="text-indigo-600 font-bold">Administralos</span>
    </p>
    <Alerta v-if="alerta.mensaje"
      :alerta="alerta"
    />
    <form action="" 
      class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
      @submit.prevent="validar"
    >
      <div class="mb-5 ">
        <label for="mascota"
          class="font-bold uppercase text-gray-700 block"
        >
          Nombre Mascota
        </label>
        <input 
          id="mascota" 
          type="text"
          placeholder="Nombre Mascota" 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          @input="$emit('update:nombre', $event.target.value)"
        />
      </div>
      <div class="mb-5 ">
        <label for="propietario"
          class="font-bold uppercase text-gray-700 block"
        >
          Nombre Propietario
        </label>
        <input 
          id="propietario" 
          type="text"
          placeholder="Nombre del Propietario" 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          @input="$emit('update:propietario', $event.target.value)"
        />
      </div>
      <div class="mb-5 ">
        <label for="email"
          class="font-bold uppercase text-gray-700 block"
        >
          Email
        </label>
        <input 
          id="email" 
          type="email"
          placeholder="Email del Propietario" 
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          @input="$emit('update:email', $event.target.value)"
        />
      </div>
      <div class="mb-5 ">
        <label for="alta"
          class="font-bold uppercase text-gray-700 block"
        >
          alta
        </label>
        <input 
          id="alta" 
          type="date"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md"
          @input="$emit('update:alta', $event.target.value)"
        />
      </div>
      <div class="mb-5 ">
        <label for="sintomas"
          class="font-bold uppercase text-gray-700 block"
        >
          Sintomas
        </label>
        <textarea
          id="sintomas"
          placeholder="Describe los sintomas"
          class="border-2 w-full p-2 mt-2 placeholder-gray-400 rounded-md h-40"
          @input="$emit('update:sintomas', $event.target.value)"
        />
      </div>
      <input 
        type="submit" 
        class="bg-indigo-600 w-full p-3 text-white uppercase font-bold hover:bg-indigo-700 cursor-pointer transition-colors"
        value="Registrar Paciente"
      >
      
    </form>
  </div>
</template>
