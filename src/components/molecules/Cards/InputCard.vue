<template>
  <div class="flex justify-end">
    <label class="inline-flex items-center mr-2">
      <input
        v-model="checked"
        type="checkbox"
        class="form-checkbox"
        checked
      />
      <span class="ml-2">Show All</span>
    </label>
    <Button
      class="bg-indigo-500 hover:bg-indigo-700"
      @click="save"
    >
      Save
    </Button>
  </div>
  <div class="mt-2 w-full">
    <Input
      v-model="text"
      placeholder="Enter somethings..."
      @keydown.enter.prevent="save"
    />
  </div>
</template>

<script lang="ts" setup>
import Input from '@/components/atoms/Input.vue'
import Button from '@/components/atoms/Button.vue'
import { ref } from 'vue'
import { useVModel } from '@vueuse/core'

const props = defineProps<{ showAll: boolean }>()

const emits = defineEmits(['save', 'update:showAll'])
const checked = useVModel(props, 'showAll', emits)

const text = ref<string>('')

const save = () => {
  emits('save', text.value)
  text.value = ''
}
</script>

<style scoped>

</style>
