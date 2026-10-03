<script lang="ts" setup>
withDefaults(defineProps<{
  type?: string
  id: string
  placeholder?: string
  label: string
}>(), {
  type: 'text'
})
const model = defineModel<string | number>()
</script>

<template>
  <div class="box">
    <label :for="id">{{ label }}</label>
    <input
      v-model="model"
      :type="type" 
      :id="id" 
      :name="id" 
      :placeholder="placeholder" 
    />
  </div>
</template>

<style scoped>
.box {
  display: flex;
  flex-direction: column;
  gap: 6px;
  margin: 1dvh;
}

label {
  color: var(--ctp-mocha-text);
  text-align: center;
}

input {
  background: var(--ctp-mocha-surface0);
  border: 1px solid var(--ctp-mocha-surface1);
  color: var(--ctp-mocha-text);
  border-radius: 6px;
  padding: 4px 12px;
  outline: none;
  transition: border-color 0.15s, box-shadow 0.15s;
}

input::placeholder {
  color: var(--ctp-mocha-overlay0);
}

input:focus {
  border-color: var(--ctp-mocha-mauve);
}

input::-webkit-inner-spin-button,
input::-webkit-outer-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  appearance: textfield;
}
</style>