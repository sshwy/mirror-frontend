<template>
  <div>
    <span>{{ props.config.name }}</span>
    <select
      v-if="props.config.type === 'select'"
      :value="modelValue"
      @change="emit('update:modelValue', ($event.target as any).value)"
    >
      <option v-for="option in config.options" :key="option.value" :value="option.value">
        {{ option.name }}
      </option>
    </select>
  </div>
</template>

<script setup lang="ts">
import { IVariableConfig } from '@/lib/variables'

const props = defineProps<{
  modelValue: string
  config: IVariableConfig
}>()

const emit = defineEmits<{
  (event: 'update:modelValue', value: string): void
}>()
</script>
