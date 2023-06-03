<script setup>
import { computed } from '@vue/reactivity';

const props = defineProps({
  alerta: {
    type: Object,
    required: true,
  },
});

const isError = computed(()=>{
    return props.alerta.tipo == 'sucess' ? 'bg-green-500':'bg-red-500'
})
</script>
<template>
  <div
  :class="isError"
    class="text-white text-center p-3 uppercase font-bold mb-3 rounded-md"
  >
    {{ alerta.mensaje }}
  </div>
</template>
