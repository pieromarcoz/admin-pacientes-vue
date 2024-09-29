<script setup>
import {computed} from "vue";

const props =defineProps({
  alerta: {
    type: Object,
    required: true
  },
})
const isError = computed(() => {
  return props.alerta.type === 'error'
})

</script>

<template>
  <div :class="isError ? 'bg-red-500' : 'bg-green-500'"
      class="text-white text-center p-3 uppercase font-bold mb-3 rounded-md">
    {{ alerta.message}}
  </div>
</template>